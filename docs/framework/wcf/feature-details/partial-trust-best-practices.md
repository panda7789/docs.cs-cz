---
title: Doporučené postupy s částečnou důvěryhodností
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: fca975ff4216384b970535273511eb07cd6ded68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="partial-trust-best-practices"></a>Doporučené postupy s částečnou důvěryhodností
Toto téma popisuje osvědčené postupy při spuštění Windows Communication Foundation (WCF) v prostředí s částečnou důvěryhodností.  
  
## <a name="serialization"></a>Serializace  
 Použít následující postupy při použití <xref:System.Runtime.Serialization.DataContractSerializer> v aplikaci částečně důvěryhodné.  
  
-   Všechny Serializovatelné typy musí být explicitně označené `[DataContract]` atribut. V prostředí s částečnou důvěryhodností nejsou podporovány následující techniky:  
  
-   Označení tříd pro Dal serializovat s příznakem <xref:System.SerializableAttribute>.  
  
-   Implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní povolit třídu řídit zpracování serializace.  
  
### <a name="using-datacontractserializer"></a>Použití DataContractSerializer  
  
-   Všechny typy označené jako `[DataContract]` atributu musí být veřejné. Není veřejné typy nelze serializovat v prostředí s částečnou důvěryhodností.  
  
-   Všechny `[DataContract]` členové serializable `[DataContract]` typ musí být veřejné. Typ s neveřejným `[DataMember]` nelze serializovat v prostředí s částečnou důvěryhodností.  
  
-   Metody, které zpracování serializace událostí (například `OnSerializing`, `OnSerialized`, `OnDeserializing`, a `OnDeserialized`) musí být deklarován jako veřejné. Ale explicitní a implicitní implementace <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> jsou podporovány.  
  
-   `[DataContract]` typy v sestavení implementována označené jako <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nesmí provádět akce související se zabezpečením v konstruktoru typu, jako <xref:System.Runtime.Serialization.DataContractSerializer> nevyvolá konstruktoru nově instanci objektu během deserializace. Konkrétně je třeba se vyhnout následující běžné techniky zabezpečení pro `[DataContract]` typy:  
  
-   Probíhá pokus o omezit částečnou důvěryhodností přístup tím, že typ konstruktor interní nebo privátní.  
  
-   Omezení přístupu k typu přidáním `[LinkDemand]` konstruktoru typu.  
  
-   Za předpokladu, že protože objekt byl úspěšně vytvořit instance, všechny ověřovací kontroly vynucováno konstruktoru mít bylo úspěšné.  
  
### <a name="using-ixmlserializable"></a>Pomocí IXmlSerializable  
 Použít následující osvědčené postupy pro typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> a se serializují pomocí <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Musí být statickou metodu implementace `public`.  
  
-   Instance metody, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní musí být `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Pomocí WCF z platformy plně důvěryhodný kód, který umožňuje volání z částečně důvěryhodné volající  
 Model zabezpečení WCF částečnou důvěryhodností předpokládá, že všechny volající veřejná metoda WCF nebo vlastnosti je spuštěn v kontextu zabezpečení (CA) přístupu kód hostitelskou aplikaci. WCF také předpokládá, že kontext zabezpečení jenom jednu aplikaci existuje pro každou <xref:System.AppDomain>, a který tento kontext je vytvořen v <xref:System.AppDomain> čas vytvoření důvěryhodného hostitele (například voláním <xref:System.AppDomain.CreateDomain%2A> nebo správcem aplikace ASP.NET).  
  
 Tento model zabezpečení platí pro uživatele zapsána aplikací, které nelze vyhodnocení další oprávnění certifikační Autority, jako je například uživatelský kód spuštěný v aplikaci ASP.NET střední vztah důvěryhodnosti. Kód plně důvěryhodná platformy (například třetí strany sestavení, které je nainstalována v globální mezipaměti sestavení a přijímá volání z částečně důvěryhodného kódu) však vyžaduje explicitní pozor, při volání do WCF jménem částečně důvěryhodné aplikace Vyhněte se zavedení chyby zabezpečení na úrovni aplikace.  
  
 Kód plné důvěryhodnosti byste neměli změna sadu oprávnění certifikační Autority aktuální vlákno (voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>) před volání rozhraní API WCF jménem částečně důvěryhodného kódu. Potvrzující, odepření nebo jinak vytváření kontextu specifické pro vlákno oprávnění, která je nezávislá kontext zabezpečení na aplikační úrovni může vést k neočekávanému chování. V závislosti na aplikaci toto chování může mít za následek ohrožení zabezpečení na úrovni aplikace.  
  
 Kód, který musí být volání do WCF pomocí kontextu specifické pro vlákno oprávnění připraveno pro zpracování těchto situacích, které může způsobit:  
  
-   Kontext zabezpečení specifické pro vlákno nemusí uchovávají po dobu trvání operace, což vede k potenciální výjimky zabezpečení.  
  
-   Interní kód WCF a také všechny zadaný uživatelem zpětná volání může spustit v kontextu zabezpečení jiný než ten, pod kterým původně zahájení hovoru. Tyto kontexty patří:  
  
    -   Kontext oprávnění aplikace.  
  
    -   Žádné oprávnění specifické pro vlákno kontextu jste předtím vytvořili pomocí jiné uživatele vlákna používaná k volání do WCF po dobu životnosti aktuálně spuštěna <xref:System.AppDomain>.  
  
 WCF zaručuje, že částečně důvěryhodného kódu, nelze získat plná oprávnění, pokud taková oprávnění jsou prosazený komponentu plně důvěryhodná před voláním do WCF veřejná rozhraní API. Však není zaručeno, že důsledky potvrzující úplný vztah důvěryhodnosti je izolovaný konkrétní vlákno, operace nebo akce uživatele.  
  
 Jako osvědčený postup, vyhněte se vytváření kontextu specifické pro vlákno oprávnění voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>. Místo toho udělit nebo odepřít oprávnění k vlastní, aplikace tak, aby žádné <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, nebo <xref:System.Security.PermissionSet.PermitOnly%2A> je vyžadován.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
