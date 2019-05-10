---
title: Doporučené postupy s částečnou důvěryhodností
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: 6c01824ef3d86600fd946e7f510b854b5138ec00
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603885"
---
# <a name="partial-trust-best-practices"></a>Doporučené postupy s částečnou důvěryhodností
Toto téma popisuje osvědčené postupy při spuštění Windows Communication Foundation (WCF) v prostředí s částečnou důvěryhodností.  
  
## <a name="serialization"></a>Serializace  
 Použijte následující postupy při používání <xref:System.Runtime.Serialization.DataContractSerializer> v částečně důvěryhodné aplikaci.  
  
- Všechny Serializovatelné typy musí být explicitně označeny pomocí `[DataContract]` atribut. V prostředí s částečnou důvěryhodností nejsou podporovány následující techniky:  
  
- Označení tříd Dal serializovat s příznakem <xref:System.SerializableAttribute>.  
  
- Implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní umožňující třídy řídit její procesu serializace.  
  
### <a name="using-datacontractserializer"></a>Pomocí třídy DataContractSerializer  
  
- Všechny typy označeny pomocí `[DataContract]` atribut musí být veřejné. Neveřejné typy nejde serializovat v částečném vztahu důvěryhodnosti prostředí.  
  
- Všechny `[DataContract]` členy v serializovatelného `[DataContract]` typ musí být veřejný. Typ se oprávnění neveřejné `[DataMember]` nejde serializovat v částečném vztahu důvěryhodnosti prostředí.  
  
- Metody, které zpracovávají události serializace (například `OnSerializing`, `OnSerialized`, `OnDeserializing`, a `OnDeserialized`) musí být deklarován jako veřejná. Ale implementace explicitního a implicitního <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> jsou podporovány.  
  
- `[DataContract]` typy, které jsou implementované v sestavení označená pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nesmí provádět akce související se zabezpečením v konstruktoru typu, jako <xref:System.Runtime.Serialization.DataContractSerializer> nevolá konstruktor objektu nově vytvořena při deserializaci. Konkrétně, je třeba se vyhnout následující běžné postupy zabezpečení pro `[DataContract]` typy:  
  
- Probíhá pokus o omezit částečným vztahem důvěryhodnosti přístup tím, že konstruktor typu interní nebo privátní.  
  
- Omezení přístupu k typu tak, že přidáte `[LinkDemand]` konstruktoru typu.  
  
- Za předpokladu, že vzhledem k tomu, že má byla úspěšně vytvořena instance objektu, mají všechny ověřovací kontroly vynucuje konstruktoru bylo úspěšné.  
  
### <a name="using-ixmlserializable"></a>Pomocí rozhraní IXmlSerializable  
 Použijte následující osvědčené postupy pro typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> a serializují pomocí <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
- <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Musí být statická metoda implementace `public`.  
  
- Instance metody, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní musí být `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Pomocí technologie WCF z plně důvěryhodné platformě kódu, který umožňuje volání od částečně důvěryhodné volající  
 Model zabezpečení částečným vztahem důvěryhodnosti WCF se předpokládá, že jakýkoli volající této WCF veřejnou metodu nebo vlastnost běží v rámci kódu access security (CAS) hostitelské aplikace. WCF také předpokládá tento kontext zabezpečení pouze jednu aplikaci existuje pro každý <xref:System.AppDomain>, a že tento kontext se stanoví při <xref:System.AppDomain> čas vytvoření důvěryhodný hostitel (například voláním <xref:System.AppDomain.CreateDomain%2A> nebo správcem aplikace technologie ASP.NET).  
  
 Tento model zabezpečení se vztahuje na uživatelem zapsaný aplikace, které nelze uplatnit další oprávnění certifikační Autority, jako je například uživatelský kód spuštěný v aplikaci ASP.NET důvěřovat střední. Však musí kód platformy plně důvěryhodné (například sestavení třetích stran, která je nainstalována v globální mezipaměti sestavení a přijímá volání od částečně důvěryhodným kódem) postupujte opatrně explicitní při volání do WCF jménem částečně důvěryhodné aplikace Vyhýbejte se ohrožení zabezpečení na úrovni aplikace.  
  
 Plně důvěryhodného kódu by měla neupravujte sada oprávnění CAS aktuálního vlákna (voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>) před voláním rozhraní API pro WCF jménem částečně důvěryhodným kódem. Uplatnění, zamítnutí nebo jinak vytvoření kontextu specifické pro vlákno oprávnění, která je nezávislá kontextu zabezpečení na úrovni aplikace může způsobit neočekávané chování. V závislosti na aplikaci toto chování může vést k ohrožení zabezpečení na úrovni aplikace.  
  
 Kód, který volá do WCF pomocí oprávnění specifické pro vlákno kontextu musí být připravena ke zpracování těchto situacích, které může způsobit:  
  
- Kontext zabezpečení specifické pro vlákno nemusí být zachována po dobu trvání operace, což vede k potenciálním bezpečnostním výjimkám.  
  
- Vnitřní kód WCF, stejně jako všechny uživatelem zadaný zpětná volání může spustit v kontextu zabezpečení než ve kterém bylo původně zahájeno volání. Kontexty patří:  
  
    - Kontext oprávnění aplikace.  
  
    - Jakýkoli kontext specifické pro vlákno oprávnění dříve vytvořené jinými vlákny uživatele použít k volání do WCF po celou dobu životnosti aktuálně běžících <xref:System.AppDomain>.  
  
 WCF zaručuje, že částečně důvěryhodným kódem nemůže získat oprávnění plné důvěryhodnosti, pokud taková oprávnění se uplatňovaný plně důvěryhodné komponenty před voláním do veřejných rozhraní API WCF. Však nezaručuje, že účinky uplatnění úplný vztah důvěryhodnosti je izolovaná na konkrétní vlákno, operace nebo akce uživatele.  
  
 Jako osvědčený postup, vyhněte se vytváření kontextu oprávnění specifické pro vlákno voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>. Místo toho udělit nebo odepřít oprávnění k aplikaci, tak, aby žádné <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, nebo <xref:System.Security.PermissionSet.PermitOnly%2A> je povinný.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
