---
title: Ukázka slabě typované serializace JSON
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: b0e9617ad5d616e8921fbf142085f2758f3e0cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006353"
---
# <a name="weakly-typed-json-serialization-sample"></a>Ukázka slabě typované serializace JSON
Při serializaci uživatelem definovaný typ daného přenosový formát nebo deserializaci přenosový formát zpět do uživatelem definovaný typ, daný uživatelský typ musí být k dispozici na službu nebo klienta. Obvykle k tomu, <xref:System.Runtime.Serialization.DataContractAttribute> atribut bude použit pro tyto typy definované uživatelem a <xref:System.Runtime.Serialization.DataMemberAttribute> atributu se použije pro jejich členy. Tento mechanismus platí i v případě práce s objekty JavaScript Object Notation (JSON), jak je popsáno v tématu [jak: Serializace a deserializace dat protokolu JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 V některých případech musí přístup služby Windows Communication Foundation (WCF) ani klienta vygeneruje služba nebo klient, který je mimo kontrolu vývojáře objekty JSON. Jako další webové služby vystavují veřejně JSON rozhraní API, může být nepraktické pro vývojáře WCF k vytvoření místního typy definované uživatelem, do které se má deserializovat libovolného objekty JSON. Tato ukázka poskytuje mechanismus, který umožňuje vývojářům WCF pro práci s objekty JSON deserializovat, libovolného bez vytvoření uživatelem definovaných typů. To se označuje jako *slabě typovaná serializace* objektů JSON, protože typ, do kterého se deserializuje objekt JSON není známý v době kompilace.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Například veřejné rozhraní API webové služby vrátí následující objekt JSON, který popisuje některé informace o uživateli služby.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 K deserializaci tohoto objektu, musí implementovat klienta WCF uživatelem definované typy.  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 To může být náročné, zejména v případě, že klient má pro zpracování více než jeden typ objektu JSON.  
  
 `JsonObject` Typ zadaný v tomto příkladu představuje slabě typovaná reprezentace deserializovaný objekt JSON. `JsonObject` spoléhá na fyzické mapování mezi objekty JSON a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] slovníky a mapování mezi poli JSON a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pole. Následující kód ukazuje `JsonObject` typu.  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 Všimněte si, že můžete "Vyhledat" objekty JSON a pole bez nutnosti pro deklaraci typu v době kompilace. Vysvětlení požadavek na nejvyšší úrovni `["root"]` objektu, naleznete v tématu [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Třídy je k dispozici pouze jako příklad. Neprošla dostatečně důkladnými a neměli byste používat v produkčním prostředí. Zřejmé nepřímo slabě typovaná serializace JSON je nedostatek bezpečnost typů, pokud pracujete s `JsonObject`.  
  
 Použít `JsonObject` typu, musíte použít klienta kontrakt <xref:System.ServiceModel.Channels.Message> jako její typ vrácené hodnoty.  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 `JsonObject` Je pak instance, jak je znázorněno v následujícím kódu.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Přebírá konstruktor <xref:System.Xml.XmlDictionaryReader>, kterého se získává <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metoda. Čtecí modul obsahuje reprezentaci v jazyce XML JSON zprávu přijatou klientem. Další informace naleznete v tématu [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program vygeneruje následující výstup:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení WeaklyTypedJson.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spuštění řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
