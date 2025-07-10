# responsiUASAlpro2025
ini adalah responsi uas alpro 
#include<iostream>
#include<fstream>

using namespace std;

const int MAX = 10;
struct Datapesawat{
	string rute[4] = {"jakarta", "bandung", "surabaya", "jogja"};
	string namamaskapai[4] = {"citilink", "lion air", "batavia", "sriwijaya"};
	int harga[4] = {500000, 750000, 1200000, 3000000};
};

class Datatiket{
	public:
		int kode;
		string namaMaskapai;
		string bandara1;
		string bandara2;
		string tanggal;
		int jam1;
		int jam2;
		int harga;
}; 

class Sistem{
	private:
	Datatiket tiket[MAX];
	Datapesawat data[MAX]; 
	int jumlahtiket = 0;
	public:
	void input(){
		int pil;
		cout<<"masukkan kode penerbangan : ";
		cin>>tiket.kode;
		
		cout<<"masukkan nama maskapai (citilink, lion air, batavia, sriwijaya) : ";
		getline(cin, tiket.namaMaskapai);
		
		cout<<"masukkan bandara asal : ";
		getline(cin, tiket.bandara1);
		
		cout<<"masukkan bandara tujuan (jakarta, bandung, surabaya, jogja): ";
		getline(cin, tiket.bandara2);
		
		cout<<"masukkan tanggal penerbangan : ";
		getline(cin, tiket.tanggal);
		
		cout<<"masukkan jam keberangkatan : "
		getline(cin, tiket.jam1);
		
		cout<<"masukkan jam kedatangan : ";
		getline(cin, tiket.jam2);
		
		jumlahtiket++;
		
	}
	
	void caridatarutepenerbangan(){
		string carirute;
		bool temukan = false;
		cout<<"masukkan rute penerbangan (jakarta, bandung, surabaya, jogja) : ";
		cin>>carirute;
		for(int i = 0; i < 4; i++ ){
			if(data.rute == carirute){
				cout<<"rute : "<<data[i].rute<<endl;
				cout<<"nama maskapai : "<<data[i].namamaskapai;
				cout<<"harga : "<<data[i].harga;
				
				temukan = true;
				cout"data ditemukan!";
			}
			
		}
		
		if(!temukan){
			cout<<"data tidak ditemukan!";
		}
	}
	
	void caridatamaskapai(){
		string carimaskapai;
		bool temukan = false;
		cout<<"masukkan rute nama maskapai (citilink, lion air, batavia, sriwijaya) : ";
		cin>>carimaskapai;
		for(int i = 0; i < 4; i++ ){
			if(data.namamaskapai == carimaskapai){
				cout<<"rute : "<<data[i].rute<<endl;
				cout<<"nama maskapai : "<<data[i].namamaskapai;
				cout<<"harga : "<<data[i].harga;
				
				temukan = true;
				cout"data ditemukan!";
			}
			
		}
		
		if(!temukan){
			cout<<"data tidak ditemukan!";
		}
	}
	
	void sortingtiketmahal(){
		for(int i = 0; i < 4; i++){
			for(int j = 0; j < 4 - 1-i; j++){
				if(data[j].harga > data[j+1].harga){
					Datapesawat temp = data[j];
					data[j] = data[j+1];
					data[j+1] = temp
				}
			}
		}
		
		for(int i = 0; i < 4; i++){
			cout<<"rute : "<<data[i].rute<<endl;
			cout<<"nama maskapai : "<<data[i].namamaskapai<<endl;
			cout<<"harga : "<<data[i].harga<<endl;
			
			cout<<endl;
		}
	}
	
	void sortingtiketmurah(){
		for(int i = 0; i < 4; i++){
			for(int j = 0; j < 4 - 1-i; j++){
				if(data[j].harga < data[j+1].harga){
					Datapesawat temp = data[j];
					data[j] = data[j+1];
					data[j+1] = temp
				}
			}
		}
		
		for(int i = 0; i < 4; i++){
			cout<<"rute : "<<data[i].rute<<endl;
			cout<<"nama maskapai : "<<data[i].namamaskapai<<endl;
			cout<<"harga : "<<data[i].harga<<endl;
			
			cout<<endl;
		}
	} 
	
	void tampilberdasarkan(){
		int pil;
		
		do{
		cout<<"1.tiket dibawah Rp. 1.000.000 : "<<endl;
		cout<<"2.tiket diatas Rp. 1.000.000 : "<<endl;
		cout<<"3.keluar!!"<<endl;
		cin>>pil;
		
		switch(pil){
			case 1: 
				for(int i = 0; i < 4; i++){
					if(data[i].harga < 1000000){
						cout<<"rute : "<<data[i].rute<<endl;
						cout<<"nama maskapai : "<<data[i].namamaskapai<<endl;
						cout<<"harga : "<<data[i].harga<<endl;
					}
				}
				break;
			case 2:
				for(int i = 0; i < 4; i++){
					if(data[i].harga > 1000000){
						cout<<"rute : "<<data[i].rute<<endl;
						cout<<"nama maskapai : "<<data[i].namamaskapai<<endl;
						cout<<"harga : "<<data[i].harga<<endl;
					}
				}
				break;
			default :
				cout<<"pilihan tidak ada!";		
		}
		
	}while(pil != 3);
}
	
	void cetaktiket(){
		
		for(int i = 0; i < 4; i++){
			for(int j = 0; j < 4 - 1-i; j++){
				if(tiket[j].kode < tiket[j+1].kode){
					Datatiket temp = tiket[j];
					tiket[j] = tiket[j+1];
					tiket[j+1] = temp
				}
			}
		}
		
		ofstream file("datatiket.txt");
		
		for(int i = 0; i < jumlahtiket; i++){
		file <<"kode penerbangan :  "<<tiket.kode;
		file <<"nama maskapai : "<<tiket.namaMaskapai;
		file <<"bandara asal :  "<<tiket.bandara1;
		file <<"bandara tujuan :  "<<tiket.bandara2;
		file <<"tanggal penerbangan :  "<<tiket.tanggal;
		file <<"jam keberangkatan :  "<<tiket.jam1;
		file <<"jam kedatangan :  "<<tiket.jam2;
		
		}
		
		file.close();
		
	}
 
 int main(){
 	Sistem s;
 	int pilihan;
 	do{
 	cout<<"=====menu======="<<endl;
 	cout<<"1.input data tiket "<<endl;
 	cout<<"2.mencari berdasarkan rute penerbangan  "<<endl;
 	cout<<"3.mencari berdasarkan maskapai penerbangan "<<endl;
 	cout<<"4.sorting berdasarkan harga tiket termahal "<<endl;
 	cout<<"5.sorting berdasarkan harga tiket termurah "<<endl;
 	cout<<"6.mencari tiket berdasarkan harga tertentu "<<endl;
 	cout<<"7.unduh tiket diurutkan kode penerbangan (txt) "<<endl;
 	cout<<"0.keluar "<<endl;
 	cout<<"pilih : ";
 	cin>>pilihan;
 	
 	switch (pilihan){
 		case 1:{
 			s.input();
			break;
		 } 
		case 2:{
		 	s.caridatarutepenerbangan();
			break;
		 }
		case 3:{
			s.caridatamaskapai();
			break;
		}
		case 4:{sdasasd
			s.sortingtiketmahal();
			break;
		}
		case 5:{
			s.sortingtiketmurah();
			break;
		}
		case 6:{
			s.tampilberdasarkan();
			break;
		}
		case 7:{
			s.cetaktiket();
			break;
		}
		default:
			cout<<"pilihan tidak ada! ";
		
	 }
 
 system("cls");
 system("pause");
}while(pilihan != 0);

	
}
