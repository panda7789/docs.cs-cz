---
title: Ukázka slabě typované serializace JSON
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: bdeaffe31ba9bced28eebcfe294fc9944e5d05d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143587"
---
# <a name="weakly-typed-json-serialization-sample"></a>Ukázka slabě typované serializace JSON
Při serializaci uživatelem definovaného typu do daného formátu drátu nebo při rekonstrukci drátového formátu zpět do uživatelem definovaného typu musí být daný typ definovaný uživatelem k dispozici ve službě i v klientovi. Obvykle k dosažení <xref:System.Runtime.Serialization.DataContractAttribute> tohoto cíle, atribut se použije <xref:System.Runtime.Serialization.DataMemberAttribute> na tyto typy definované uživatelem a atribut je použit a jejich členy. Tento mechanismus platí také při práci s objekty JavaScript Object Notation (JSON), jak je popsáno v tématu [Jak: Serializovat a rekonstruovat JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 V některých případech musí služba WCF (Windows Communication Foundation) nebo klient přistupovat k objektům JSON generovaným službou nebo klientem, který je mimo kontrolu vývojáře. Jako další webové služby veřejně vystavit JSON rozhraní API, může být nepraktické pro wcf vývojář vytvořit místní uživatelem definované typy, do kterých chcete rekonstruovat libovolné objekty JSON. Tato ukázka poskytuje mechanismus, který umožňuje vývojářům WCF pracovat s rekonstruovanými, libovolnými objekty JSON bez vytváření typů definovaných uživatelem. To se označuje jako *slabě typovaná serializace* objektů JSON, protože typ, do kterého objekt JSON deserializuje, není v době kompilace znám.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Například rozhraní API veřejné webové služby vrátí následující objekt JSON, který popisuje některé informace o uživateli služby.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Chcete-li tento objekt rekonstruovat, musí klient WCF implementovat následující uživatelem definované typy.  
  
```csharp  
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
  
 To může být těžkopádné, zejména v případě, že klient má zpracovat více než jeden typ objektu JSON.  
  
 Typ `JsonObject` poskytované této ukázce zavádí slabě typované reprezentace deserialized JSON objektu. `JsonObject`závisí na přirozeném mapování mezi objekty JSON a slovníky rozhraní .NET Framework a na mapování mezi poli JSON a poli rozhraní .NET Framework. Následující kód ukazuje `JsonObject` typ.  
  
```csharp  
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
  
 Všimněte si, že můžete "procházet" JSON objekty a pole bez nutnosti deklarovat jejich typ v době kompilace. Vysvětlení požadavku na objekt nejvyšší úrovně `["root"]` naleznete v tématu [Mapování mezi jazyky JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> Třída `JsonObject` je k dispozici pouze jako příklad. Nebyla důkladně testována a neměla by být používána v produkčním prostředí. Zřejmým důsledkem slabě typované serializace JSON je nedostatek `JsonObject`bezpečnosti typů při práci s .  
  
 Chcete-li `JsonObject` použít typ, smlouvy <xref:System.ServiceModel.Channels.Message> o operaci klienta musí použít jako jeho návratový typ.  
  
```csharp  
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
  
 Je `JsonObject` pak vytvořena instance, jak je znázorněno v následujícím kódu.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 Konstruktor `JsonObject` trvá <xref:System.Xml.XmlDictionaryReader>, který je <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> získán metodou. Čtečka obsahuje xml reprezentaci zprávy JSON přijaté klientem. Další informace naleznete v tématu [Mapování mezi jazyky JSON a JAZYKEM XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program vytváří následující výstup:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení WeaklyTypedJson.sln, jak je popsáno v [sestavení ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte řešení.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
