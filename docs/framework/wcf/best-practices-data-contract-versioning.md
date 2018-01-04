---
title: "Osvědčené postupy: Správa verzí kontraktů dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78373d482aaaa0121a6c2708f543188d9cc9464d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-data-contract-versioning"></a>Osvědčené postupy: Správa verzí kontraktů dat
Toto téma obsahuje osvědčené postupy pro vytváření dat smlouvy, které můžete snadno vyvíjet se v čase. [!INCLUDE[crabout](../../../includes/crabout-md.md)]kontrakty dat naleznete v tématech v [pomocí kontrakty dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Poznámka: v ověřování schématu  
 V hovoříte o Správa verzí kontraktů dat, je důležité si uvědomit, že data smlouvy schématu exportované sadou [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] nemá žádné podporu správy verzí, než fakt, že ve výchozím nastavení jsou označená jako volitelná elementy.  
  
 To znamená, že i nejběžnější Správa verzí scénář, jako je například přidávání nového člena dat, nelze implementovat způsobem, který je bezproblémové s ohledem na daném schématu. Novější verze kontraktu dat (s nového datového člena, např.) nelze ověřit pomocí staré schématu.  
  
 Existují však mnoho scénářů, ve kterých není vyžaduje striktní schématu dodržování předpisů. Mnoho webových služeb platformy, včetně [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a XML webové služby vytvořené pomocí technologie ASP.NET, není ve výchozím nastavení provádět ověřování schématu a proto tolerovat dodatečné prvky, které nejsou popsané schéma. Při práci s takové platformy, jsou usnadňují implementaci mnoho scénářů správy verzí.  
  
 Proto existují dvě sady dat smlouvy verze: jeden pro scénáře, kde platnosti striktní schématu je důležité, a další nastavení pro scénáře, když není nastaven.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Správa verzí, pokud je nutné použít ověřování schématu  
 Pokud platnosti striktní schématu je nutná všech pokynů (nové starý a starého na nové), kontrakty dat považovat za neměnné. Pokud je třeba Správa verzí, se vytvoří nový kontrakt dat, s jiným názvem nebo obor názvů, a kontrakt služby pomocí datový typ musí být verzí odpovídajícím způsobem.  
  
 Například nákupní objednávka zpracování kontrakt služby s názvem `PoProcessing` s `PostPurchaseOrder` operace přebírá parametr, který vyhovuje `PurchaseOrder` kontrakt dat. Pokud `PurchaseOrder` kontrakt musí změnit, je třeba vytvořit nové smlouvy dat, tedy `PurchaseOrder2`, což zahrnuje změny. Pak je nutné zajistit Správa verzí na úrovni kontrakt služby. Například tak, že vytvoříte `PostPurchaseOrder2` operaci, která přebírá `PurchaseOrder2` parametr, nebo vytvořením `PoProcessing2` kontrakt služby kde `PostPurchaseOrder` trvá operace `PurchaseOrder2` kontrakt dat.  
  
 Všimněte si, že změny v kontraktech dat, které odkazují jiné kontrakty dat také rozšířit vrstva modelu služby. Například v předchozím scénáři `PurchaseOrder` kontrakt dat není potřeba změnit. Obsahuje však data členem `Customer` kontrakt dat, který naopak obsažená data členem `Address` kontrakt dat, který je třeba změnit. V takovém případě je potřeba vytvořit `Address2` kontrakt dat s požadované změny `Customer2` kontrakt dat, který obsahuje `Address2` – datový člen a `PurchaseOrder2` kontrakt dat, který obsahuje `Customer2` – datový člen. Jako v předchozím případě by mohl být verzí také kontrakt služby.  
  
 I když v těchto příkladech jsou názvy měnit (přidáním "2"), doporučuje se změnit obory názvů namísto názvů přidáním nové obory názvů s číslem verze nebo datum. Například `http://schemas.contoso.com/2005/05/21/PurchaseOrder` kontrakt dat změní na `http://schemas.contoso.com/2005/10/14/PurchaseOrder` kontrakt dat.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]Osvědčené postupy: [verze služby](../../../docs/framework/wcf/service-versioning.md).  
  
 V některých případech striktní schématu dodržování předpisů pro zprávy odeslané aplikace musí zaručit, ale nelze spoléhat na příchozí zprávy, které mají být úplně schématu kompatibilní. V tomto případě je nebezpečí, že příchozí zprávy může obsahovat nadbytečné data. Nadbytečné hodnoty jsou uloženy a vrácený [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a proto výsledkem odesílány zprávy neplatné schéma. K tomuto problému nedošlo, by měl být vypnuté funkci odezvy. Chcete-li to provést dvěma způsoby.  
  
-   Neimplementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní na žádném z vašich typů.  
  
-   Použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut vaše kontrakt služby s <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost nastavena na hodnotu `true`.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]odezvy, najdete v části [kontrakty dat dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Správa verzí, když se nevyžaduje ověření schématu  
 Dodržování předpisů striktní schématu se zřídka vyžaduje. Řada platforem tolerovat dodatečné prvky, které nejsou popsané ve schématu. Také to je dovoleno, úplnou sadu funkcí popsaných v [Správa verzí kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) a [kontrakty dat dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) lze použít. Doporučuje se podle následujících pokynů.  
  
 Některé z pokynů musí být sledována přesně tak, aby bylo možné odesílat nové verze typu, kde je očekávána starší nebo odeslat starý, kde je očekávána novým. Další pokyny nejsou bezpodmínečně nutné, ale jsou zde uvedeny, protože může být ovlivněno budoucí verze schématu.  
  
1.  Nepokoušejte se kontrakty verze dat podle typu dědičnosti. Pokud chcete vytvořit novější verze, změnit kontrakt dat na existující typ nebo vytvořte nový typ nesouvisejícími.  
  
2.  Použití dědičnosti společně s kontrakty dat je povolen, za předpokladu, že dědičnosti není používána jako mechanismus Správa verzí a dodržíte určitá pravidla. Pokud je typ odvozena z určité základní typ, neprovádějte je odvozena od různých základní typ v budoucí verzi (Pokud má stejné datové kontrakt). Jedinou výjimkou je: typ můžete vložit do hierarchie mezi typ kontraktu dat a jeho základní typ, ale jenom v případě, že neobsahuje datových členů, stejné názvy jako ostatní členové všechny možné verze jiné typy v hierarchii. Obecně platí pomocí datových členů se stejnými názvy s různou úrovní stejné hierarchie dědičnosti může vést k vážným Správa verzí problémům a je nutno.  
  
3.  Počínaje první verze součásti kontraktu dat vždy implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> povolit odezvy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kontraktů dat s dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Pokud jeden nebo více verzí typu mít vydání bez implementace tohoto rozhraní, implementaci v příští verzi typu.  
  
4.  V novějších verzích neměňte název kontraktu dat nebo obor názvů. Pokud změníte název nebo obor názvů typu základní kontrakt dat, je nutné zachovat název kontraktu dat a oboru názvů pomocí příslušné mechanismy, jako <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]pojmenování, najdete v části [názvy datových kontraktů](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  V novějších verzích Neměňte názvy všech datových členů. Pokud změníte název pole, vlastnost nebo událostí základní datový člen, použijte `Name` vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> zachovat stávající název člena data.  
  
6.  V novějších verzích neměňte typ žádné pole, vlastnost nebo základní datový člen tak, aby smlouvy Výsledná data pro tento člen změny dat událostí. Mějte na paměti, které typy rozhraní jsou rovnocenná <xref:System.Object> pro účely určení kontrakt očekávaná data.  
  
7.  V novějších verzích, neměňte pořadí existující data členů úpravou <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.  
  
8.  V novějších verzích mohou být přidány nové datových členů. Vždy postupujte tato pravidla:  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Vlastnost by měla být vždy ponechány na jeho výchozí hodnotu `false`.  
  
    2.  Pokud výchozí hodnota je `null` nebo nula pro člena nepřijatelný, metody zpětného volání by je třeba zadat pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute> zajistit přiměřené výchozí v případě, že člen není k dispozici v příchozím datovém proudu. [!INCLUDE[crabout](../../../includes/crabout-md.md)]zpětné volání, najdete v části [verze proti chybám zpětná volání serializace tolerantní](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  `Order` Vlastnost `DataMemberAttribute` se má použít k zajištění všech nově přidaných datových členů zobrazení po existující datových členů. Doporučený způsob to to vypadá takto: žádná z datových členů v první verzi kontrakt dat by měl mít jejich `Order` sadu vlastností. Všechny členy data přidána do verze 2 kontrakt dat by měl mít jejich `Order` vlastnost nastavena na hodnotu 2. Všechny členy data přidána do verze 3 kontrakt dat by měl mít jejich `Order` nastavena na hodnotu 3 a tak dále. Je přípustné mít více než jednoho člena dat se nastaví na stejnou `Order` číslo.  
  
9. Neodebírejte datových členů v novějších verzích, i v případě <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost byla ponechány na jeho výchozí vlastnost `false` v předchozích verzích.  
  
10. Neměňte `IsRequired` vlastnost v žádné stávající data členy z verze na verzi.  
  
11. Pro členy požadovaná data (kde `IsRequired` je `true`), se nezmění `EmitDefaultValue` vlastnost z verze na verzi.  
  
12. Nepokoušejte se vytváření hierarchií větvenou správy verzí. To znamená, že by měla být vždy cestu minimálně jeden směr z libovolné verze na jakoukoli jinou verzi pomocí pouze změny, které jsou povolené podle těchto pokynů.  
  
     Například pokud verze 1 kontraktu dat osoba obsahuje pouze název datového člena, je byste je neměli vytvářet verze 2a kontraktu přidání pouze stáří člen a verze 2b přidání pouze člena adresy. Má z 2a 2b zahrnovat stáří odeberete a přidáte adresu; přejdete v opačným směrem by mít za následek odebrání adresy a přidání stáří. Odebrat členy není povolen podle těchto pokynů.  
  
13. Obecně byste neměli vytvářet nové podtypů existující typy kontraktů dat v nové verzi vaší aplikace. Podobně byste je neměli vytvářet nové kontrakty dat, které se používají místo data, která členy deklarovaný jako objekt, nebo jako typy rozhraní. Vytvoření tyto nové třídy je povoleno pouze v případě, že znáte, můžete přidat nové typy do seznamu známých typů všech instancí staré aplikace. Ve verzi 1 aplikace může například mít LibraryItem datový typ s knihy kontraktu a data novinách smlouvy podtypů. LibraryItem by pak znamenalo, známé typy seznam, který obsahuje knihy a novinách. Předpokládejme, že přidáte typu časopis nyní ve verzi 2, což je podtypem LibraryItem. Pokud odešlete instance časopis z verze 2 verze 1, kontrakt dat časopis nebyl nalezen v seznamu známých typů a je vyvolána výjimka.  
  
14. Neměli přidat nebo odebrat členy výčtu mezi verzemi. Členové výčtu by neměl také přejmenovat, pokud použijete vlastnost názvu na `EnumMemberAttribute` atribut zachovat jejich názvy v datovém modelu kontrakt stejné.  
  
15. Kolekce se v datovém modelu kontrakt, jak je popsáno v zaměňovat [typy kolekcí v kontraktech dat](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). To umožňuje vysoký stupeň flexibilitu. Ale ujistěte se, že neměnit nechtěně typu kolekce v jiný zaměňovat způsobem v závislosti na verzi. Například neměňte z kolekce neupravené (tedy bez `CollectionDataContractAttribute` atribut) k přizpůsobené jedné nebo vlastní kolekce neupravené jeden. Navíc neměňte vlastnosti na `CollectionDataContractAttribute` na verzi. Jedinou změnou povolených je přidání vlastnosti Name nebo Namespace, pokud došlo ke změně názvu nebo obor názvů základní typ kolekce a je třeba, aby jeho data smlouvy názvem a oborem názvů stejný jako předchozí verze.  
  
 Některé zde uvedené pokyny můžete bezpečně ignorovat při použít zvláštní okolnosti. Ujistěte se, že rozumíte plně serializace, deserializace a schéma mechanismy související se situací před odchylují od podle pokynů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 [Použití kontraktů dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Správa verzí kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Názvy kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Kontrakty dat s dopřednou kompatibilitou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Zpětná volání serializace tolerantní k verzím](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
