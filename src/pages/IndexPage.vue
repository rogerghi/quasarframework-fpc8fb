<template>
  <q-layout view="hHh lpR fFf">
    <q-header flat class="bg-white text-black">
      <q-toolbar>
        <q-toolbar-title class="text-weight-light" style="padding-left: 5px">
          Form Persetujuan
        </q-toolbar-title>

        <q-space></q-space>

        <div class="q-pa-md q-gutter-sm">
          <q-btn icon="mdi-keyboard-return" color="red" label="Return"></q-btn>
          <q-btn
            icon="mdi-account-reactivate"
            color="orange"
            label="Disposition"
          ></q-btn>
          <q-btn icon="mdi-content-save" color="blue" label="Save"></q-btn>
          <q-btn icon="mdi-send" color="teal" label="Send"></q-btn>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="left" side="left"> </q-drawer>

    <q-drawer show-if-above v-model="right" side="right"> </q-drawer>

    <q-page-container>
      <router-view>
        <div class="row">
          <div class="col">
            <div class="q-gutter-md q-pt-md q-pb-lg">
              <q-input
                filled
                v-model="name"
                label="Nomor Surat"
                hint="Mohon diisi dengan nomor surat dari pimpinan"
              ></q-input>

              <q-input
                filled
                v-model="date"
                mask="date"
                :rules="['date']"
                label="Tanggal Surat"
                hint="Mohon diisi dengan tanggal dari surat pimpinan"
              >
                <template v-slot:append>
                  <q-icon name="event" class="cursor-pointer">
                    <q-popup-proxy
                      ref="qDateProxy"
                      transition-show="scale"
                      transition-hide="scale"
                    >
                      <q-date v-model="date">
                        <div class="row items-center justify-end">
                          <q-btn
                            v-close-popup
                            label="Close"
                            color="primary"
                            flat
                          ></q-btn>
                        </div>
                      </q-date>
                    </q-popup-proxy>
                  </q-icon>
                </template>
              </q-input>

              <q-input
                v-model="text"
                filled
                type="textarea"
                label="Hal"
                placeholder="Ketik disini.."
                hint="Mohon diisi sesuai dengan tujuan pengajuan ini"
              ></q-input>
            </div>
          </div>
          <div class="col">
            <div class="q-pa-md">
              <div class="q-gutter-md items-start">
                <q-file
                  v-model="files"
                  label="Lampiran surat persetujuan"
                  filled
                  counter
                  :counter-label="counterLabelFn"
                  max-files="1"
                  multiple
                >
                  <template v-slot:prepend>
                    <q-icon name="attach_file"></q-icon>
                  </template>
                </q-file>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <q-toggle
            v-model="accept"
            label="Saya menyetujui, bahwa data informasi dan lampiran tersebut sudah benar."
          ></q-toggle>
        </div>
      </router-view>
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue';

const count = ref(0);

const min = -5;
const max = 5;
</script>
