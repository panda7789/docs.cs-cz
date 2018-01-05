---
title: "Doporučené postupy s částečnou důvěryhodností"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 817f7aeeb7adece1c375bb8b0cc455a17fb54185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="partial-trust-best-practices"></a>Doporučené postupy s částečnou důvěryhodností
Toto téma popisuje osvědčené postupy při spuštění [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] v prostředí s částečnou důvěryhodností.  
  
## <a name="serialization"></a>Serializace  
 Použít následující postupy při použití <xref:System.Runtime.Serialization.DataContractSerializer> v aplikaci částečně důvěryhodné.  
  
-   Všechny Serializovatelné typy musí být explicitně označené `[DataContract]` atribut. V prostředí s částečnou důvěryhodností nejsou podporovány následující techniky:  
  
-   Označení tříd pro Dal serializovat s příznakem <xref:System.SerializableAttribute>.  
  
-   Implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní povolit třídu řídit zpracování serializace.  
  
### <a name="using-datacontractserializer"></a>Použití DataContractSerializer  
  
-   Všechny typy označené jako `[DataContract]` atributu musí být veřejné. Není veřejné typy nelze serializovat v prostředí s částečnou důvěryhodností.  
  
-   Všechny `[DataContract]` členové serializable `[DataContract]` typ musí být veřejné. Typ s neveřejným `[DataMember]` nelze serializovat v prostředí s částečnou důvěryhodností.  
  
-   Metody, které zpracování serializace událostí (například `OnSerializing`, `OnSerialized`, `OnDeserializing`, a `OnDeserialized`) musí být deklarován jako veřejné. Ale explicitní a implicitní implementace <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> jsou podporovány.  
  
-   `[DataContract]`typy v sestavení implementována označené jako <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nesmí provádět akce související se zabezpečením v konstruktoru typu, jako <xref:System.Runtime.Serialization.DataContractSerializer> nevyvolá konstruktoru nově instanci objektu během deserializace. Konkrétně je třeba se vyhnout následující běžné techniky zabezpečení pro `[DataContract]` typy:  
  
-   Probíhá pokus o omezit částečnou důvěryhodností přístup tím, že typ konstruktor interní nebo privátní.  
  
-   Omezení přístupu k typu přidáním `[LinkDemand]` konstruktoru typu.  
  
-   Za předpokladu, že protože objekt byl úspěšně vytvořit instance, všechny ověřovací kontroly vynucováno konstruktoru mít bylo úspěšné.  
  
### <a name="using-ixmlserializable"></a>Pomocí IXmlSerializable  
 Použít následující osvědčené postupy pro typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> a se serializují pomocí <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Musí být statickou metodu implementace `public`.  
  
-   Instance metody, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní musí být `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Pomocí WCF z platformy plně důvěryhodný kód, který umožňuje volání z částečně důvěryhodné volající  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model zabezpečení částečnou důvěryhodností předpokládá, že všechny volající [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veřejné metody nebo vlastnosti běží v kontextu zabezpečení (CA) přístupu kód hostitelskou aplikaci. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také předpokládá, že kontext zabezpečení jenom jednu aplikaci existuje pro každou <xref:System.AppDomain>, a který tento kontext je vytvořen v <xref:System.AppDomain> čas vytvoření důvěryhodného hostitele (například voláním <xref:System.AppDomain.CreateDomain%2A> nebo správcem aplikace ASP.NET).  
  
 Tento model zabezpečení platí pro uživatele zapsána aplikací, které nelze vyhodnocení další oprávnění certifikační Autority, jako je například uživatelský kód spuštěný v aplikaci ASP.NET střední vztah důvěryhodnosti. Kód plně důvěryhodná platformy (například třetí strany sestavení, které je nainstalována v globální mezipaměti sestavení a přijímá volání z částečně důvěryhodného kódu) však vyžaduje explicitní pozor, při volání do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jménem částečně důvěryhodné aplikace, aby se zabránilo zavedení chyby zabezpečení na úrovni aplikace.  
  
 Kód plné důvěryhodnosti byste neměli změna sadu oprávnění certifikační Autority aktuální vlákno (voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>) před voláním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozhraní API jménem částečně důvěryhodného kódu. Potvrzující, odepření nebo jinak vytváření kontextu specifické pro vlákno oprávnění, která je nezávislá kontext zabezpečení na aplikační úrovni může vést k neočekávanému chování. V závislosti na aplikaci toto chování může mít za následek ohrožení zabezpečení na úrovni aplikace.  
  
 Kód, který volá do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] použitím odlišného kontextu, specifické pro vlákno oprávnění musí být připraveno pro zpracování těchto situacích, které může způsobit:  
  
-   Kontext zabezpečení specifické pro vlákno nemusí uchovávají po dobu trvání operace, což vede k potenciální výjimky zabezpečení.  
  
-   Interní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kódu a také všechny zadaný uživatelem zpětná volání může spustit v kontextu zabezpečení jiný než ten, pod kterým původně zahájení hovoru. Tyto kontexty patří:  
  
    -   Kontext oprávnění aplikace.  
  
    -   Žádné oprávnění specifické pro vlákno kontextu jste předtím vytvořili pomocí jiné uživatele vlákna používaná k volání do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] po dobu životnosti aktuálně spuštěna <xref:System.AppDomain>.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zaručuje, že částečně důvěryhodného kódu, nelze získat plná oprávnění, pokud taková oprávnění jsou prosazený komponentu plně důvěryhodná před voláním do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veřejná rozhraní API. Však není zaručeno, že důsledky potvrzující úplný vztah důvěryhodnosti je izolovaný konkrétní vlákno, operace nebo akce uživatele.  
  
 Jako osvědčený postup, vyhněte se vytváření kontextu specifické pro vlákno oprávnění voláním <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, nebo <xref:System.Security.PermissionSet.Deny%2A>. Místo toho udělit nebo odepřít oprávnění k vlastní, aplikace tak, aby žádné <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, nebo <xref:System.Security.PermissionSet.PermitOnly%2A> je vyžadován.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
