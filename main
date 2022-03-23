#include <stdio.h>
#include <stdlib.h>

struct Urunler{
    int ID;
    char *urunAdi;
    int alisFiyati;
    int satisFiyati;
    int alimTarihi;
    int sonKar;
    int stok;
    struct Urunler  *next;
    struct Urunler *prev;
}urun;
struct Urunler *head = NULL;
struct Urunler *tail = NULL;
int lastID = 1;
int urunSayisi=0;
///urun listesi
void urunListesi()
{
    struct Urunler *u = head;
    if(u !=NULL)
    {
        printf("%d adet urun listelendi\n",urunSayisi);
    while (u != NULL)
    {

        urunYazdir(u);
        u=u->next;
    }
    }
    else
        printf("Hic bir urun bulunamadi\n");

}

///urun bulma
struct Urunler *urunBul(int ID)
{
    struct Urunler *u = head;
    while (u != NULL)
    {
        if(u->ID == ID)
        break;
        else
        u = u->next;
    }
    return u;
}


///urun eklme
struct Urunler *urunEkle(char *name,int alisFiyati, int satisFiyati,int alimTarihi,int stock)
{
    struct Urunler *u = (struct Urunler*)malloc(sizeof(struct Urunler));
    u->ID = lastID++;
    u->urunAdi=strdup(name);
    u->alisFiyati = alisFiyati;
    u->satisFiyati = satisFiyati;
    u->alimTarihi = alimTarihi;
    u->stok = stock;
    u->prev=tail;
    urunYazdir(u);
    urunSayisi++;
    if(head == NULL)
    {
        u->next=NULL;
        u->prev=NULL;
        head = u;
        tail = u;
        return u;
    }
    tail->next = u;
    tail = u;
    return u;
}

///urun silme
void *urunSil(int ID)
{
    struct Urunler *u = urunBul(ID);
    if(u==NULL)
        printf("urun bulunamadi\n");

    else if(u==head)
    {
        if(u==tail)
        {
            u==NULL;
        }
        else
        {
            u=head->next;
            u->prev=NULL;
            head=u;
        }
    }
    else if(u==tail)
    {
        u=tail->prev;
        u->next=NULL;
        tail=u;
    }
    else
    {
        u->prev->next=u->next;
        u->next->prev=u->prev;
        u=NULL;
    }
    urunSayisi--;
    printf("urun basariyla silindi\n");
}

///kar hesaplama
void karHesapla()
{
    struct Urunler *u;
  int toplamkar=0;
  for(u=head;u<tail;u++)
  {
      printf("urunlerden kariniz sirasiyla :%.d\n",u->sonKar);
  }
  for(u=head;u<tail;u++)
  {
      toplamkar+=u->sonKar;
  }
  printf("Toplam kariniz :%d",toplamkar);
}

///urun satis
void urunSat(int ID,int adet)
{
    int kar;
    struct Urunler *u =urunBul(ID);
    u->stok-=adet;
    kar=u->satisFiyati-u->alisFiyati;
    kar=kar*adet;
    u->sonKar+=kar;
    printf("Urun basariyla %d adet satildi",adet);
}

///urun guncelleme!!!
void *urunGuncelle(int ID,char* urunAdi,int alisFiyati, int satisFiyati,int alimTarihi,int stok)
{
    struct Urunler *u = urunBul(ID);
    if(u==NULL)
    {
        printf("Urun %d bulunamadi\n",ID);
        return NULL;
    }
    else
    {
    //strcpy(u->urunAdi,urunAdi);
    u->urunAdi=strdup(urunAdi);
    u->alisFiyati = alisFiyati;
    u->satisFiyati = satisFiyati;
    u->alimTarihi=alimTarihi;
    u->stok=stok;
    printf("Urun %d Guncellendi\n",ID);
    urunYazdir(u);
    }
}
///urun yazdirma
void urunYazdir(struct Urunler *u){
if(u!=NULL)
    {
        printf("UrunID: %d , Urun Adi: %s , Alis Fiyati: %d , Satis Fiyati: %d ,Alim Tarihi: %d, Son Kar: %d , Stok: %d\n",
               u->ID,u->urunAdi , u->alisFiyati, u->satisFiyati, u->alimTarihi, u->sonKar, u->stok);
    }
}


///urun satin alma
void urunAl(int ID,int adet)
{
    struct Urunler *u= urunBul(ID);
    int tarih;
    printf("Lutfen alim tarihi giriniz\n");
    scanf("%d",&tarih);
    u->alimTarihi=tarih;
    u->stok+=adet;
    printf("%d adet urun eklendi\n",adet);
}
int main()
{
    int a=1, stock, t, ID, adet;
    int af, sf;
    char *name=malloc(sizeof(char)*15);

    printf("Hosgeldiniz\n");
    while(a!=0)
    {
        printf("\nYapabileceginiz islemler altta belirtilmistir\nUrunleri gormek icin 1\nUrun bulmak icin 2\nUrun eklemek icin 3\nUrun silmek icin 4\nKar hesaplamak icin 5\nUrun satmak icin 6\nUrun satin almak icin 7\nUrun guncellemek icin 8\n\nCikis icin 0\n");
        scanf("%d",&a);
        switch(a)
        {
            case 0:
                break;
            case 1:
                urunListesi(urun);
                break;
            case 2:
                printf("Lutfen bulunacak urun kodunu girin\n");
                scanf("%d",&ID);
                struct Urunler *u = urunBul(ID);
                urunYazdir(u);
                break;
            case 3:
                printf("lutfen eklencek urunun adini girin\n");
                scanf("%s",name);
                printf("Lutfen eklencek urunun alim fiyatini girin\n");
                scanf("%d",&af);
                printf("Lutfen eklenecek urunun satim fiyatini girin\n");
                scanf("%d",&sf);
                printf("Lutfen eklenecek urunun son alim tarihi girin\n");
                scanf("%d",&t);
                printf("Lutfen eklenecek urunun stok adetini girin\n");
                scanf("%d",&stock);
                urunEkle(name,af,sf,t,stock);
                break;
            case 4:
                printf("Lutfen silinecek urun kodunu girin\n");
                scanf("%d",&ID);
                urunSil(ID);
                break;
            case 5:
                karHesapla();
                break;
            case 6:
                printf("Lutfen satmak istediginiz urunun IDsini giriniz\n");
                scanf("%d",&ID);
                printf("Kac adet sattiginizi giriniz\n");
                scanf("%d",&adet);
                urunSat(ID,adet);
                break;
            case 7:
                printf("Lutfen almak istediginiz urunun IDsini giriniz\n");
                scanf("%d",&ID);
                printf("Kac adet almak istediginizi giriniz\n");
                scanf("%d",&adet);
                urunAl(ID,adet);
                break;
            case 8:
                printf("Lutfen guncellemek istediginiz urunun IDsini giriniz\n");
                scanf("%d",&ID);
                printf("Lutfen yeni adini giriniz\n");
                scanf("%s",&name);
                printf("Lutfen yeni alim fiyatini giriniz\n");
                scanf("%d",&af);
                printf("Lutfen yeni satin alim fiyatini giriniz\n");
                scanf("%d",&sf);
                printf("Lutfen yeni alim tarihini giriniz\n");
                scanf("%d",&t);
                printf("Lutfen yeni stok adetini giriniz\n");
                scanf("%d",&stock);
                urunGuncelle(ID,name,af,sf,t,stock);
                break;
            default:
                printf("Lutfen gecerli bir sayi tuslayiniz\n");
                break;
        }
    }
    printf("Basariyla Cikis Yaptiniz\n");

    return 0;
}
