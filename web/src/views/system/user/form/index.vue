<script setup lang="ts">
import { ref } from "vue";
import ReCol from "@/components/ReCol";
import { formRules } from "../utils/rule";
import { FormProps } from "../utils/types";
import { usePublicHooks } from "../../hooks";

const props = withDefaults(defineProps<FormProps>(), {
  formInline: () => ({
    title: "新增",
    nickname: "",
    username: "",
    password: "",
    allQuota: 0,
    email: "",
    enable: true,
    group: "default"
  })
});

const ruleFormRef = ref();
const { switchStyle } = usePublicHooks();
const newFormInline = ref(props.formInline);

function getRef() {
  return ruleFormRef.value;
}

defineExpose({ getRef });
</script>

<template>
  <el-form
    ref="ruleFormRef"
    :model="newFormInline"
    :rules="formRules"
    label-width="82px"
  >
    <el-row :gutter="30">
      <re-col :value="12" :xs="24" :sm="24">
        <el-form-item label="用户昵称" prop="nickname">
          <el-input
            v-model="newFormInline.nickname"
            clearable
            placeholder="请输入用户昵称"
          />
        </el-form-item>
      </re-col>
      <re-col
        v-if="newFormInline.title === '新增'"
        :value="12"
        :xs="24"
        :sm="24"
      >
        <el-form-item label="用户名称" prop="username">
          <el-input
            v-model="newFormInline.username"
            clearable
            placeholder="请输入用户名称"
          />
        </el-form-item>
      </re-col>

      <re-col
        v-if="newFormInline.title === '新增'"
        :value="12"
        :xs="24"
        :sm="24"
      >
        <el-form-item label="用户密码" prop="password">
          <el-input
            v-model="newFormInline.password"
            clearable
            placeholder="请输入用户密码"
          />
        </el-form-item>
      </re-col>
      <re-col :value="12" :xs="24" :sm="24">
        <el-form-item label="邮箱" prop="email">
          <el-input
            v-model="newFormInline.email"
            clearable
            placeholder="请输入邮箱"
          />
        </el-form-item>
      </re-col>

      <re-col :value="12" :xs="24" :sm="24">
        <el-form-item label="余额" prop="allQuota">
          <el-input
            v-model="newFormInline.allQuota"
            clearable
            placeholder="请输入余额"
          />
        </el-form-item>
      </re-col>
      <!--      <re-col :value="12" :xs="24" :sm="24">-->
      <!--        <el-form-item label="用户性别">-->
      <!--          <el-select-->
      <!--            v-model="newFormInline.sex"-->
      <!--            placeholder="请选择用户性别"-->
      <!--            class="w-full"-->
      <!--            clearable-->
      <!--          >-->
      <!--            <el-option-->
      <!--              v-for="(item, index) in sexOptions"-->
      <!--              :key="index"-->
      <!--              :label="item.label"-->
      <!--              :value="item.value"-->
      <!--            />-->
      <!--          </el-select>-->
      <!--        </el-form-item>-->
      <!--      </re-col>-->

      <!--      <re-col :value="12" :xs="24" :sm="24">-->
      <!--        <el-form-item label="归属部门">-->
      <!--          <el-cascader-->
      <!--            v-model="newFormInline.parentId"-->
      <!--            class="w-full"-->
      <!--            :options="newFormInline.higherDeptOptions"-->
      <!--            :props="{-->
      <!--              value: 'id',-->
      <!--              label: 'name',-->
      <!--              emitPath: false,-->
      <!--              checkStrictly: true-->
      <!--            }"-->
      <!--            clearable-->
      <!--            filterable-->
      <!--            placeholder="请选择归属部门"-->
      <!--          >-->
      <!--            <template #default="{ node, data }">-->
      <!--              <span>{{ data.name }}</span>-->
      <!--              <span v-if="!node.isLeaf"> ({{ data.children.length }}) </span>-->
      <!--            </template>-->
      <!--          </el-cascader>-->
      <!--        </el-form-item>-->
      <!--      </re-col>-->
      <re-col
        v-if="newFormInline.title === '新增'"
        :value="12"
        :xs="24"
        :sm="24"
      >
        <el-form-item label="用户状态">
          <el-switch
            v-model="newFormInline.enable"
            inline-prompt
            :active-value="true"
            :inactive-value="false"
            active-text="启用"
            inactive-text="停用"
            :style="switchStyle"
          />
        </el-form-item>
      </re-col>

      <!--      <re-col>-->
      <!--        <el-form-item label="备注">-->
      <!--          <el-input-->
      <!--            v-model="newFormInline.remark"-->
      <!--            placeholder="请输入备注信息"-->
      <!--            type="textarea"-->
      <!--          />-->
      <!--        </el-form-item>-->
      <!--      </re-col>-->
    </el-row>
  </el-form>
</template>
