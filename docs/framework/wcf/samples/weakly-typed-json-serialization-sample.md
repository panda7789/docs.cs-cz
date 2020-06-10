---
title: Ukázka slabě typované serializace JSON
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: a503878f1cbb60090b648da8dfec741edbf02d1b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602320"
---
# <a name="weakly-typed-json-serialization-sample"></a>Ukázka slabě typované serializace JSON
Při serializaci uživatelsky definovaného typu do daného formátu nebo deserializaci formátu přenosu zpět do uživatelsky definovaného typu musí být daný uživatelsky definovaný typ k dispozici jak v rámci služby, tak i v klientovi. Obvykle k tomu je <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit pro tyto uživatelsky definované typy a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut je použit na své členy. Tento mechanismus platí také při práci s objekty JavaScript Object Notation (JSON), jak je popsáno v tématu [Postupy: serializace a deserializace dat JSON](../feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 V některých scénářích musí služba Windows Communication Foundation (WCF) nebo klient přistupovat k objektům JSON generovaným službou nebo klientem, který se nachází mimo ovládací prvek vývojáře. V případě, že více webových služeb zveřejňuje rozhraní API JSON, může být pro vývojáře WCF nepraktické vytvořit místní uživatelsky definované typy, do kterých se mají deserializovat libovolné objekty JSON. Tato ukázka poskytuje mechanismus, který vývojářům WCF umožňuje pracovat s deserializovanými a libovolnými objekty JSON, aniž by museli vytvářet uživatelsky definované typy. To se označuje jako *slabě typované serializace* objektů JSON, protože typ, ve kterém je deserializace objektu JSON, není v době kompilace znám.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Například rozhraní API veřejné webové služby vrací následující objekt JSON, který popisuje některé informace o uživateli služby.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 K deserializaci tohoto objektu musí klient WCF implementovat následující uživatelsky definované typy.  
  
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
  
 To může být náročné, zejména v případě, že klient musí zpracovat více než jeden typ objektu JSON.  
  
 `JsonObject`Typ poskytnutý touto ukázkou zavádí slabě typované reprezentace objektu JSON deserializovatelné. `JsonObject`spoléhá na přirozené mapování mezi objekty JSON a .NET Framework slovníku a mapování mezi poli JSON a .NET Framework poli. Následující kód ukazuje `JsonObject` typ.  
  
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
  
 Všimněte si, že můžete procházet objekty JSON a pole bez nutnosti deklarovat jejich typ v době kompilace. Vysvětlení požadavku na objekt nejvyšší úrovně `["root"]` naleznete v tématu [mapování mezi JSON a XML](../feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> `JsonObject`Třída je k dispozici pouze jako příklad. Není důkladně testován a neměl by se používat v produkčním prostředí. Zjevným nedostatečně typované serializace JSON je nedostatečná typ při práci s `JsonObject` .  
  
 Chcete-li použít `JsonObject` typ, kontrakt klientské operace musí použít <xref:System.ServiceModel.Channels.Message> jako svůj návratový typ.  
  
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
  
 `JsonObject`Pak je vytvořena instance, jak je znázorněno v následujícím kódu.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject`Konstruktor přebírá <xref:System.Xml.XmlDictionaryReader> metodu, která je získána prostřednictvím <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metody. Čtecí modul obsahuje reprezentaci XML zprávy JSON, kterou klient přijal. Další informace naleznete v tématu [mapování mezi JSON a XML](../feature-details/mapping-between-json-and-xml.md).  
  
 Program vytvoří následující výstup:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení WeaklyTypedJson. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Spusťte řešení.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
