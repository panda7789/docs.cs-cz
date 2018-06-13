---
title: Ukázka slabě typované serializace JSON
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: 294c00bd18b5fabba5baa20770fd593031a98994
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805717"
---
# <a name="weakly-typed-json-serialization-sample"></a>Ukázka slabě typované serializace JSON
Při serializaci uživatelem definovaný typ daného přenosový formát nebo deserializaci přenosový formát zpět do uživatelem definovaný typ, daný uživatelem definovaný typ musí být k dispozici na službu a klienta. Obvykle k tomu <xref:System.Runtime.Serialization.DataContractAttribute> tyto uživatelem definované typy je použit atribut a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut se používá k jejich členové. Tento mechanismus platí i v případě práce s objekty jazyka JavaScript Object Notation (JSON), jak je popsáno v tématu [postup: serializaci a deserializaci JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 V některých případech potřebuje přístup objekty JSON vygenerovaných služba nebo klienta, který je mimo kontrolu vývojáře služby Windows Communication Foundation (WCF) nebo klienta. Protože více webových služeb veřejně vystavit JSON rozhraní API, může stát nepraktické pro vývojáře WCF vytvořit místní uživatelem definované typy do kterého mají být deserializována libovolné objekty JSON. Tato ukázka poskytuje mechanismus, který umožňuje vývojářům WCF pro práci s objekty JSON deserializovat, libovolný bez vytvoření uživatelem definované typy. To se označuje jako *slabě typované serializace* objektů JSON, protože typ, do kterého deserializuje objekt JSON není známý v době kompilace.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Například veřejný Web service API vrátí následující objekt JSON, který popisuje některé informace o uživateli služby.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 K deserializaci tento objekt, musí implementovat klienta WCF uživatelem definované typy.  
  
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
  
 To může být náročná, obzvláště pokud má klient pro zpracování více než jeden typ objektu JSON.  
  
 `JsonObject` Typ poskytované Tato ukázka představuje slabě typované reprezentace deserializovaný objekt JSON. `JsonObject` spoléhá na fyzické mapování mezi objekty JSON a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] slovník a mapování mezi JSON pole a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pole. Následující kód ukazuje `JsonObject` typu.  
  
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
  
 Všimněte si, že můžete "Vyhledat" JSON objekty a pole, aniž by bylo nutné deklarovat jejich typů v době kompilace. Další informace o požadavku na nejvyšší úrovni `["root"]` objektu, podívejte se na téma [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Třídy se poskytuje pouze jako příklad. Neprošla dostatečně důkladnými a neměl by se používat v produkčním prostředí. Zřejmé vyplývá slabě typované serializace JSON je nedostatek bezpečnost typů, při práci s `JsonObject`.  
  
 Použít `JsonObject` typu, musí používat klienta operaci kontrakt <xref:System.ServiceModel.Channels.Message> jako její návratový typ.  
  
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
  
 `JsonObject` Je pak instanci, jak je znázorněno v následujícím kódu.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Konstruktor přijímá <xref:System.Xml.XmlDictionaryReader>, který byl získán prostřednictvím <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metoda. Čtečka obsahuje reprezentaci XML zprávy JSON přijatých klientem. Další informace naleznete v tématu [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program vytvoří následující výstup:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení WeaklyTypedJson.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Viz také
