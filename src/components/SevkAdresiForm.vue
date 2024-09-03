<template>
  <div class="container shadow-lg p-4 mb-5 bg-body rounded">
    <h4>Sevk Adresi</h4>
    <hr />
    <form>
      <!-- Ad ve Ülke -->
      <div class="row mb-4">
        <div class="col-md-4">
          <label for="ad" class="form-label">Ad</label>
          <multiselect
            v-model="ad"
            :options="availableNames"
            placeholder="Ad giriniz"
          ></multiselect>
        </div>
        <div class="col-md-4">
          <label for="ulke" class="form-label">Ülke</label>
          <multiselect
            v-model="ulke"
            :options="ulkeler"
            placeholder="Ülke seçiniz"
          ></multiselect>
        </div>
        <div class="col-md-4">
          <label for="il" class="form-label">İl/İlçe</label>
          <multiselect
            v-model="il"
            :options="iller"
            placeholder="İl/İlçe seçiniz"
          ></multiselect>
        </div>
      </div>

      <!-- Adres -->
      <div class="row mb-3">
        <div class="col-md-12">
          <label for="adres" class="form-label">Adres</label>
          <input
            type="text"
            class="form-control"
            id="adres"
            v-model="adres"
            placeholder="Adres giriniz"
          />
        </div>
      </div>

      <!-- Vergi No ve Vergi Dairesi -->
      <div class="row mb-3">
        <div class="col-md-6">
          <label for="vergiNo" class="form-label">Vergi No</label>
          <input
            type="text"
            class="form-control"
            id="vergiNo"
            v-model="vergiNo"
            placeholder="Vergi No giriniz"
          />
        </div>
        <div class="col-md-6">
          <label for="vergiDairesi" class="form-label">Vergi Dairesi</label>
          <input
            type="text"
            class="form-control"
            id="vergiDairesi"
            v-model="vergiDairesi"
            placeholder="Vergi Dairesi giriniz"
          />
        </div>
      </div>

      <!-- Latitude ve Longitude çap -->
      <div class="row mb-3">
        <div class="col-md-4">
          <label for="latitude" class="form-label">Latitude</label>
          <input
            type="text"
            class="form-control"
            id="latitude"
            v-model="latitude"
            placeholder="Latitude giriniz"
          />
        </div>
        <div class="col-md-4">
          <label for="longitude" class="form-label">Longitude</label>
          <input
            type="text"
            class="form-control"
            id="longitude"
            v-model="longitude"
            placeholder="Longitude giriniz"
          />
        </div>
        <div class="col-md-4">
          <label for="cap" class="form-label">Çap</label>
          <input
            type="text"
            class="form-control"
            id="cap"
            v-model="cap"
            placeholder="Çap giriniz"
          />
        </div>
      </div>

      <!-- tanım Departman ve posta kodu -->
      <div class="row mb-3">
        <div class="col-md-4">
          <label for="postaKodu" class="form-label">Tanım</label>
          <input
            type="text"
            class="form-control"
            id="postaKodu"
            v-model="postaKodu"
            placeholder="Tanım kodu"
          />
        </div>

        <div class="col-md-4">
          <label for="departman" class="form-label">Departman</label>
          <multiselect
            v-model="departman"
            :options="departmanlar"
            placeholder="Departman seçiniz"
            :multiple="true"
          ></multiselect>
        </div>

        <div class="col-md-4">
          <label for="postaKodu" class="form-label">Posta Kodu</label>
          <input
            type="text"
            class="form-control"
            id="postaKodu"
            v-model="postaKodu"
            placeholder="Posta Kodu giriniz"
          />
        </div>
      </div>

      <!-- E-posta ve Mal Kabul-ve Kaza/Güvenli Nokta -->
      <div class="row mb-3">
        <div class="col-md-4">
          <label for="telefonNo" class="form-label">Telefon No</label>
          <input
            type="text"
            class="form-control"
            id="telefonNo"
            v-model="telefonNo"
            placeholder="Telefon No giriniz"
          />
        </div>
        <div class="col-md-4">
          <label for="email" class="form-label">E-Posta Adresi</label>
          <input
            type="email"
            class="form-control"
            id="email"
            v-model="email"
            placeholder="E-posta adresi giriniz"
          />
        </div>
        <div class="col-md-4">
          <label for="kaza" class="form-label">Kaza/Güvenlik Nokta</label>
          <multiselect
            v-model="kaza"
            :options="kazalar"
            placeholder="Ara"
          ></multiselect>
        </div>

        <div class="col-md-6 d-flex align-items-center">
          <input type="checkbox" id="malKabul" v-model="malKabul" />
          <label for="malKabul" class="form-label ms-2"
            >Mal Kabul Tanımlı Mı?</label
          >
        </div>
      </div>

      <!-- Aktif / Pasif  -->
      <div class="row mb-3">
        <div class="col-md-12">
          <label for="aktifPasif" class="form-label">Aktif / Pasif</label>
          <select class="form-select" id="aktifPasif" v-model="aktifPasif">
            <option value="Aktif">Aktif</option>
            <option value="Pasif">Pasif</option>
          </select>
        </div>
      </div>
    </form>

    <div class="mt-5">
      <h5>Müşteri</h5>
      <a href="#" @click="showModal = true" class="text-danger mb-3 d-block"
        >Ekle</a
      >
      <table class="table table-bordered">
        <thead>
          <tr>
            <th>Firma</th>
            <th>Adres Kodu</th>
            <th>İşlem</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in firmalar" :key="index">
            <td>{{ item.firma }}</td>
            <td>{{ item.kod }}</td>
            <td>
              <button class="btn btn-danger" @click="removeItem(index)">
                Sil
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Modal -->
    <div v-if="showModal" class="modal" tabindex="-1">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Sevk Adresi & Firma</h5>
            <button
              type="button"
              class="btn-close"
              @click="showModal = false"
            ></button>
          </div>
          <div class="modal-body">
            <div class="mb-3">
              <label for="firma" class="form-label">Firma</label>
              <multiselect
                v-model="selectedFirma"
                :options="availableNames"
                placeholder="Firma seçiniz"
              ></multiselect>
            </div>
            <div class="mb-3">
              <label for="kod" class="form-label">Kod</label>
              <input
                type="text"
                class="form-control"
                id="kod"
                v-model="selectedKod"
                placeholder="Kod giriniz"
              />
            </div>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              @click="showModal = false"
            >
              Kapat
            </button>
            <button type="button" class="btn btn-success" @click="addFirma">
              Ekle
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import Multiselect from "vue-multiselect";
import "vue-multiselect/dist/vue-multiselect.ssr.css";

export default {
  components: {
    Multiselect,
  },
  data() {
    return {
      ad: null,
      availableNames: [], // Autocomplete için örnek veri
      ulkeler: [],
      ulke: null,
      iller: [
        "Ankara/Kazan-TR0620",
        "İstanbul/Ataşehir-TR0340",
        "İzmir/Foça-TR0432",
      ],
      il: "Ankara/Kazan-TR0620",

      adres:
        "Ankara Lojistik Üssü B Blok No:3-4,Bitik,06980 Kahramankazan/Ankara,Türkiye",
      vergiNo: "",
      vergiDairesi: "",
      latitude: "40.110812",
      longitude: "32.6031917",
      cap: "1",
      postaKodu: "06980",
      departmanlar: ["Yurt İçi", "Yurt Dışı"], // Dropdown örneği
      departman: "Yurt İçi",
      telefonNo: "",
      email: "",
      malKabul: false,
      aktifPasif: "Aktif",
      kazaGuvenliNokta: "",
      kazalar: ["Beylikdüzü", "Ataşehir"],
      kaza: null,
      showModal: false, // Modal gösterimini kontrol eder
      selectedFirma: null, // Modal'da seçilen firma
      selectedKod: "", // Modal'da girilen kod
      firmalar: [], // Tabloda gösterilecek firmalar
    };
  },

  created() {
    this.fetchAvailableNames();
    this.fetchCountries();
  },
  methods: {
    async fetchAvailableNames() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users"
        );
        this.availableNames = response.data.map((user) => user.name); // Kullanıcı adlarını al
      } catch (error) {
        console.error("Error fetching names:", error);
      }
    },
    async fetchCountries() {
      try {
        // REST Countries API'den ülke bilgilerini çekiyoruz
        const response = await axios.get("https://restcountries.com/v3.1/all");
        // Ülke isimlerini `ulkeler` dizisine aktarıyoruz
        this.ulkeler = response.data.map((country) => country.name.common);
      } catch (error) {
        console.error("Error fetching countries:", error);
      }
    },
    addFirma() {
      if (this.selectedFirma && this.selectedKod) {
        this.firmalar.push({
          firma: this.selectedFirma,
          kod: this.selectedKod,
        });
        this.selectedFirma = null;
        this.selectedKod = "";
        this.showModal = false;
      }
    },
    removeItem(index) {
      this.firmalar.splice(index, 1);
    },
  },
};
</script>
<style scoped>
.container {
  max-width: 900px;
}
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-dialog {
  max-width: 500px;
  width: 100%;
}
input[type="text"],
select {
  border-radius: 5px;
  border: 1px solid #ced4da;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  color: #495057;
}

label {
  font-weight: bold;
  margin-bottom: 0.5rem;
}
</style>
