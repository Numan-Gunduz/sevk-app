<!-- 
<template>

  <div class="container mt-5">
    <h3>Sevk Adresi</h3>
    <hr />
    <form>
      <div class="row mb-3">
        <div class="col-md-4">
          <label for="ad" class="form-label">Ad</label>
          <input
            type="text"
            class="form-control"
            id="ad"
            v-model="ad"
            placeholder="Ad giriniz"
            required
          />
        </div>
        <div class="col-md-4">
          <label for="ulke" class="form-label">Ülke</label>
          <select class="form-select" id="ulke" v-model="ulke" required>
            <option v-for="ulke in ulkeler" :key="ulke.id" :value="ulke" >
              {{ ulke.ad }}
            </option>
          </select>
        </div>
        <div class="col-md-4">
          <label for="il" class="form-label">İl/İlçe</label>
          <select class="form-select" id="il" v-model="il" required>
            <option v-for="il in iller" :key="il.id" :value="il">
              {{ il.ad }}
            </option>
          </select>
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-12">
          <label for="adres" class="form-label">Adres</label>
          <input type="text" class="form-control" id="adres" v-model="adres" required />
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-6">
          <label for="vergiNo" class="form-label">Vergi No</label>
          <input
            type="text"
            class="form-control"
            id="vergiNo"
            v-model="vergiNo"
          />
        </div>
        <div class="col-md-6">
          <label for="vergiDairesi" class="form-label">Vergi Dairesi</label>
          <input
            type="text"
            class="form-control"
            id="vergiDairesi"
            v-model="vergiDairesi"
          />
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4">
          <label for="latitude" class="form-label">Latitude</label>
          <input
            type="text"
            class="form-control"
            id="latitude"
            v-model="latitude"
          />
        </div>
        <div class="col-md-4">
          <label for="longitude" class="form-label">Longitude</label>
          <input
            type="text"
            class="form-control"
            id="longitude"
            v-model="longitude"
          />
        </div>
        <div class="col-md-4">
          <label for="cap" class="form-label">Çap</label>
          <input type="text" class="form-control" id="cap" v-model="cap" />
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4">
          <label for="latitude" class="form-label">Tanım</label>
          <input type="text" class="form-control" id="tanım" v-model="tanım" />
        </div>
        <div class="col-md-4">
          <label for="departman" class="form-label">Departman</label>
          <select class="form-select" id="departman" v-model="departman">
            <option value="Yurt İçi">Yurt İçi</option>
            <option value="Yurt Dışı">Yurt Dışı</option>
          </select>
        </div>
        <div class="col-md-4">
          <label for="postaKodu" class="form-label">Posta Kodu</label>
          <input
            type="text"
            class="form-control"
            id="postaKodu"
            v-model="postaKodu"
          />
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4">
          <label for="telefonNo" class="form-label">Telefon No</label>
          <input
            type="number"
            class="form-control"
            id="telefonNo"
            v-model="telefonNo"
          />
        </div>
        <div class="col-md-4">
          <label for="email" class="form-label">E-Posta Adresi</label>
          <input type="email" class="form-control" id="email" v-model="email" />
        </div>
        <div class="col-md-4">
          <label for="kazaGuvenliNokta" class="form-label"
            >Kaza/Güvenli Nokta</label
          >
          <input
            type="text"
            class="form-control"
            id="kazaGuvenliNokta"
            v-model="kazaGuvenliNokta"
          />
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4 d-flex align-items-center">
          <input type="checkbox" id="malKabul" v-model="malKabul" />
          <label for="malKabul" class="form-label ms-2"
            >Mal Kabul Tanımlı Mı?</label
          >
        </div>
        <div class="col-md-3">
          <label for="aktifPasif" class="form-label">Aktif / Pasif</label>
          <select class="form-select" id="aktifPasif" v-model="aktifPasif">
            <option value="Aktif">Aktif</option>
            <option value="Pasif">Pasif</option>
          </select>
        </div>
      </div>

      <button type="submit" class="btn btn-primary">Kaydet</button>
    </form>
  </div>
</template>


<script>

export default {
  data() {
    return {
      ad: "",
      ulkeler: [
        { id: 1, ad: "Türkiye" },
        { id: 2, ad: "ABD" },
      ],
      ulke: null,
      iller: [
        { id: 1, ad: "Ankara" },
        { id: 2, ad: "İstanbul" },
      ],
      il: null,
      adres: "",
      vergiNo: "",
      vergiDairesi: "",
      latitude: "",
      longitude: "",
      cap: "",
      postaKodu: "",
      departman: "Yurt İçi",
      telefonNo: "",
      email: "",
      malKabul: false,
      aktifPasif: "Aktif",
      kazaGuvenliNokta: "",
    };
  },
};
</script>

<style scoped>
.container {
  max-width: 800px;
}
</style> -->

<template>

    <div class="container shadow-lg p-4 mb-5 bg-body rounded">
      <h4>Sevk Adresi</h4>
      <hr>
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
              @input="onCityChange"
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

        <!-- E-posta ve Mal Kabul -->
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
            <label for="kazaGuvenliNokta" class="form-label"
              >Kaza/Güvenli Nokta</label
            >
            <input
              type="text"
              class="form-control"
              id="kazaGuvenliNokta"
              v-model="kazaGuvenliNokta"
              placeholder="Kaza/Güvenli Nokta giriniz"
            />
          </div>

          <div class="col-md-6 d-flex align-items-center">
            <input type="checkbox" id="malKabul" v-model="malKabul" />
            <label for="malKabul" class="form-label ms-2"
              >Mal Kabul Tanımlı Mı?</label
            >
          </div>
        </div>

        <!-- Aktif / Pasif ve Kaza/Güvenli Nokta -->
        <div class="row mb-3">
          <div class="col-md-12">
            <label for="aktifPasif" class="form-label">Aktif / Pasif</label>
            <select class="form-select" id="aktifPasif" v-model="aktifPasif">
              <option value="Aktif">Aktif</option>
              <option value="Pasif">Pasif</option>
            </select>
          </div>
        </div>

        <button type="submit" class="btn btn-primary">Kaydet</button>
      </form>
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
      iller: ["Ankara", "İstanbul", "İzmir"],
      il: null,
      adres: "bosna hersek mahallesi kermeş sokak no 2",
      vergiNo: "",
      vergiDairesi: "",
      latitude: "",
      longitude: "",
      cap: "",
      postaKodu: "6500",
      departmanlar: ["Yurt İçi", "Yurt Dışı"], // Dropdown örneği
      departman: null,
      telefonNo: "",
      email: "",
      malKabul: false,
      aktifPasif: "Aktif",
      kazaGuvenliNokta: "",
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
  },
};
</script>

<style scoped>
.container {
  max-width: 800px;
  box-shadow: 40px;
}
</style>
