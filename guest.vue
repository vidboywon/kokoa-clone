<template>
  <v-container>
    <v-card-title class="pb-2 text-h4 font-weight-bold">
      ゲスト情報登録
    </v-card-title>
    <v-card-title class="pa-0">
      <strong
        class="pl-5 red--text"
      >
        *
      </strong>
      <span>
        は必須項目です。
      </span>
    </v-card-title>
    <!-- フォーム始まり -->
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
    >
      <!-- 基本情報 -->
      <v-card
        class="ma-5"
        outlined
      >
        <v-card-subtitle class="text-h6 font-weight-bold">
          基本情報
        </v-card-subtitle>
        <v-row no-gutters>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>氏名(漢字)</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-text-field>
          </v-col>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>氏名(カナ)</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-text-field>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              label="氏名(ローマ字)"
            />
          </v-col>
          <v-col cols="2">
            <v-select
              outlined
              dense
              class="mx-5"
              :items="gender"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>性別</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>所属会社</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-text-field>
          </v-col>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              label="出向元会社名"
            />
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="6">
            <v-text-field
              outlined
              dense
              class="mx-5"
              label="座席番号"
            />
          </v-col>
        </v-row>
      </v-card>
      <!-- 契約情報 -->
      <v-card
        class="ma-5"
        outlined
      >
        <v-card-subtitle class="text-h6 font-weight-bold">
          契約情報
        </v-card-subtitle>
        <v-row no-gutters>
          <!-- DATE1 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu1"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date1"
                  class="mx-5"
                  label="初出社日"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  :rules="requiredRules"
                  v-on="on"
                >
                  <template slot="label">
                    <span>初出社日</span>
                    <strong
                      class="red--text"
                    >
                      *
                    </strong>
                  </template>
                </v-text-field>
              </template>
              <v-date-picker
                v-model="date1"
                @input="menu1 = false"
              />
            </v-menu>
          </v-col>
          <!-- DATE3 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu3"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date3"
                  class="mx-5"
                  label="契約開始日"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  :rules="requiredRules"
                  v-on="on"
                >
                  <template slot="label">
                    <span>契約開始日</span>
                    <strong
                      class="red--text"
                    >
                      *
                    </strong>
                  </template>
                </v-text-field>
              </template>
              <v-date-picker
                v-model="date3"
                @input="menu3 = false"
              />
            </v-menu>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <!-- DATE4 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu4"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date4"
                  class="mx-5"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  :rules="requiredRules"
                  v-on="on"
                >
                  <template slot="label">
                    <span>契約終了日</span>
                    <strong
                      class="red--text"
                    >
                      *
                    </strong>
                  </template>
                </v-text-field>
              </template>
              <v-date-picker
                v-model="date4"
                @input="menu4 = false"
              />
            </v-menu>
          </v-col>
          <!-- DATE5 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu5"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date5"
                  class="mx-5"
                  label="退社日"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  v-on="on"
                />
              </template>
              <v-date-picker
                v-model="date5"
                @input="menu5 = false"
              />
            </v-menu>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <!-- DATE6 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu6"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date6"
                  class="mx-5"
                  label="CA管理登録日"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  v-on="on"
                />
              </template>
              <v-date-picker
                v-model="date6"
                @input="menu6 = false"
              />
            </v-menu>
          </v-col>
          <!-- DATE7 -->
          <v-col
            cols="６"
          >
            <v-menu
              v-model="menu7"
              :close-on-content-click="false"
              :nudge-right="40"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date7"
                  class="mx-5"
                  label="最終出社日"
                  outlined
                  dense
                  readonly
                  v-bind="attrs"
                  prepend-inner-icon="mdi-calendar"
                  v-on="on"
                />
              </template>
              <v-date-picker
                v-model="date7"
                @input="menu7 = false"
              />
            </v-menu>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <!-- 取引先 -->
          <v-col
            cols="6"
          >
            <v-select
              class="mx-5"
              outlined
              dense
              label="契約先(取引先)"
              :items="mock"
            />
          </v-col>
        </v-row>
      </v-card>
      <!-- 詳細情報 -->
      <v-card
        class="ma-5"
        outlined
      >
        <v-card-subtitle class="text-h6 font-weight-bold">
          雇用形態ゲスト詳細情報(労務更新情報)
        </v-card-subtitle>
        <v-row no-gutters>
          <v-col cols="8">
            <v-select
              class="mx-5"
              dense
              outlined
              :items="mock"
            >
              <template slot="label">
                <span>参画プロジェクト</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
          <v-col cols="4">
            <v-select
              class="mx-5"
              dense
              outlined
              :items="mock"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>勤務体形</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="4">
            <v-select
              class="mx-5"
              dense
              outlined
              :items="selectValue"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>ネームプレートの有無</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
          <v-col cols="4">
            <v-select
              class="mx-5"
              dense
              outlined
              :items="selectValue"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>バルーンの有無</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
          <v-col cols="4">
            <v-select
              class="mx-5"
              dense
              outlined
              :items="selectValue"
              :rules="requiredRules"
            >
              <template slot="label">
                <span>ゲストカードの有無</span>
                <strong
                  class="red--text"
                >
                  *
                </strong>
              </template>
            </v-select>
          </v-col>
        </v-row>
      </v-card>
      <!-- 備考 -->
      <v-card
        class="ma-5 pb-5"
        outlined
      >
        <v-card-subtitle class="text-h6 font-weight-bold">
          備考(通知時使用)
        </v-card-subtitle>
        <v-textarea
          class="ma-5"
          counter="1000"
          outlined
          clearable
          clear-icon="mdi-eraser"
          label="総務への備考"
          auto-grow
          :rules="lengthRules"
        />
        <v-textarea
          class="ma-5"
          counter="1000"
          outlined
          clearable
          clear-icon="mdi-eraser"
          label="人事への備考"
          auto-grow
          :rules="lengthRules"
        />
        <v-textarea
          class="ma-5"
          counter="1000"
          outlined
          clearable
          clear-icon="mdi-eraser"
          label="システム管理への備考"
          auto-grow
          :rules="lengthRules"
        />
      </v-card>
      <!-- ボタン -->
      <v-container class="text-right pr-5">
        <v-btn class="mr-3">
          キャンセル
        </v-btn>
        <v-btn
          :disabled="!valid"
          color="primary"
          @click="validate"
        >
          新規登録
        </v-btn>
      </v-container>
    </v-form>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    // dropdown
    gender: ['男', '女'],
    selectValue: ['有',　'無'],
    mock: ['mock1', 'mock2', 'mock3'],
    // date
    date1: null,
    date3: null,
    date4: null,
    date5: null,
    date6: null,
    date7: null,
    menu1: false,
    menu3: false,
    menu4: false,
    menu5: false,
    menu6: false,
    menu7: false,
    //Rules
    valid: true,
    requiredRules: [value => !!value || '必須項目です'],
    lengthRules: [v => v.length < 25 || '最大1000文字までです'],
  }),
  //
  computed: {
    computedDateFormatted () {
      return this.formatDate(this.date)
    },
  },

  watch: {
    date (val) {
      this.dateFormatted = this.formatDate(this.date)
    },
  },
  methods: {
    validate () {
      this.$refs.form.validate()
    },
    formatDate (date) {
      if (!date) return null

      const [year, month, day] = date.split('-')
      return `${year}/${month}/${day}`
    }
  }
}
</script>

<style>

</style>
