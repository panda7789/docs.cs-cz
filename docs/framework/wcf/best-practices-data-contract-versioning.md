---
title: 'Doporučené postupy: Správa verzí kontraktů dat'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 544ecc3827a698f92ec29855f1e000fce1907386
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409468"
---
# <a name="best-practices-data-contract-versioning"></a>Doporučené postupy: Správa verzí kontraktů dat
Toto téma obsahuje osvědčené postupy pro vytváření dat smlouvy, které v průběhu času můžete snadno vyvíjejí. Další informace o kontraktech dat, najdete v tématech v [kontraktů dat pomocí](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Poznámka týkající se ověřování schématu  
 V zabývat Správa verzí kontraktů dat, je důležité si uvědomit, že schéma dat smlouvu exportovat Windows Communication Foundation (WCF) nemá žádné podporou správy verzí, než je skutečnost, že ve výchozím nastavení jsou označeny jako volitelné elementy.  
  
 To znamená, že i nejběžnější scénáře správy verzí jako je například přidávání nových datový člen nejde implementovat způsobem, který je bezproblémové s ohledem na dané schéma. Novější verze kontraktu dat. (s nový datový člen, například) nelze ověřit pomocí staré schématu.  
  
 Existují však mnoho scénářů, ve kterých striktní schéma dodržování předpisů se nevyžaduje. Mnoho webových služeb platformy, včetně WCF a XML webových služeb vytvořené pomocí ASP.NET, není ve výchozím nastavení provádět ověřování schématu a proto tolerovat dodatečné prvky, které nebyly popsány pomocí schématu rozhraní. Při práci s tyto platformy, se snadněji implementovat řadu scénářů správy verzí.  
  
 Proto existují dvě sady dat smlouvy pokyny pro správu verzí: jeden pro scénáře, kde je důležité, striktní schéma platnosti a další nastavení pro scénáře, když není nastaven.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Správa verzí, pokud je nutné použít ověřování schématu  
 Pokud ve všech směrech (nové starého a staré – nové) se vyžaduje striktní schéma platnosti, kontrakty dat by měl být považován za neměnitelný. Pokud správy verzí je potřeba, nový datový kontrakt by měl být vytvořen s jiným názvem nebo obor názvů, a kontrakt služby pomocí datový typ by měl být označené verzí odpovídajícím způsobem.  
  
 Například nákupní objednávku zpracovává kontrakt služby s názvem `PoProcessing` s `PostPurchaseOrder` operace přebírá parametr, který odpovídá `PurchaseOrder` kontraktu dat. Pokud `PurchaseOrder` smlouvy musí změnit, je třeba vytvořit nové kontraktu dat, to znamená, `PurchaseOrder2`, což zahrnuje změny. Potom musí umět zpracovat správy verzí na úrovni kontraktu služby. Například tak, že vytvoříte `PostPurchaseOrder2` operace, která přebírá `PurchaseOrder2` parametr, nebo tak, že vytvoříte `PoProcessing2` kontrakt služby kde `PostPurchaseOrder` operace přebírá `PurchaseOrder2` kontraktu dat.  
  
 Všimněte si, že změny v kontraktech dat, které odkazují jiné kontraktů dat rozšířit také vrstva modelu služby. Například v předchozím scénáři `PurchaseOrder` kontraktu dat. není potřeba změnit. Však obsahuje datový člen třídy `Customer` kontraktu dat, která dále obsaženy datový člen třídy `Address` kontraktu dat, které je třeba změnit. V takovém případě je potřeba vytvořit `Address2` kontraktu dat s požadované změny `Customer2` kontraktu dat, která obsahuje `Address2` datový člen a `PurchaseOrder2` kontraktu dat, která obsahuje `Customer2` datový člen. Stejně jako v předchozím případě by mohl být označené verzí také kontrakt služby.  
  
 I když v těchto příkladech jsou názvy změnit (přidáním "2"), doporučujeme změnit obory názvů namísto názvů přidáním nové obory názvů s číslo verze nebo datum. Například `http://schemas.contoso.com/2005/05/21/PurchaseOrder` kontraktu dat se změní `http://schemas.contoso.com/2005/10/14/PurchaseOrder` kontraktu dat.  
  
 Další informace najdete v tématu Doporučené postupy: [Správa verzí služby](../../../docs/framework/wcf/service-versioning.md).  
  
 V některých případech musí zajistit dodržování předpisů striktní schéma pro zprávy odeslané aplikací ale nelze spoléhat na příchozí zprávy, které mají být přísně schématu nedodržující předpisy. V takovém případě hrozí, že příchozí zprávy může obsahovat nadbytečná data. Nadbytečné hodnoty jsou uloženy a vrácené WCF, jejichž výsledkem tedy schéma neplatný zprávy odesílané. Tomuto problému zabráníte tak, by měla být funkce verzemi vypnuta. Existují dva způsoby, jak to provést.  
  
-   Neprovádějte implementaci <xref:System.Runtime.Serialization.IExtensibleDataObject> na některý z typů rozhraní.  
  
-   Použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut vaše kontrakt služby s <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> nastavenou na `true`.  
  
 Další informace o verzemi najdete v tématu [kontraktů dat dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Správa verzí při ověřování schématu se nevyžaduje  
 Striktní schéma dodržování předpisů se jen zřídka vyžaduje. Řada platforem tolerovat dodatečné prvky, které nejsou popsané ve schématu. Za předpokladu, to je dovoleno, úplná sada funkcí popsaných v [Správa verzí kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) a [kontraktů dat dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) lze použít. Následující pokyny jsou vhodné.  
  
 Některé pokyny musí následovat přesně tak, aby bylo možné odesílat nové verze typu, kde je očekávána starší nebo odeslat staré heslo, kde je očekávána novou. Další pokyny nejsou bezpodmínečně nutné, ale jsou zde uvedeny, protože mohou být ovlivněny budoucnost schématu.  
  
1.  Nepokoušejte se verzí kontraktů dat podle typu dědičnosti. K vytvoření novější verze, změnit kontraktu dat na existujícím typu nebo vytvořte nový typ nesouvisející.  
  
2.  Použití dědičnosti spolu s kontrakty dat je povoleno, za předpokladu, že dědičnosti se nepoužívá jako mechanismus správy verzí a nepoužijí určitá pravidla. Pokud typ je odvozen od určité základní typ, Nedělejte ji odvodit z různých základního typu v budoucí verzi (Pokud se stejná data smlouvy). Existuje jedna výjimka: typ můžete vložit do hierarchie mezi typ kontraktu dat a jeho základní typ, ale pouze v případě, že neobsahuje datové členy pomocí stejné názvy jako ostatní členové všechny možné verze z ostatních typů v hierarchii. Obecně platí pomocí datové členy se stejnými názvy na různých úrovních stejné hierarchii dědičnosti může vést k problémům vážné správy verzí a mělo by se vyhnout.  
  
3.  Od první verze kontraktu dat, vždy implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> umožňující verzemi. Další informace najdete v tématu [kontraktů dat dopřednou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Vydání jeden nebo více verzemi typu bez implementace tohoto rozhraní implementaci v příští verzi typu.  
  
4.  V novějších verzích neměňte název kontraktu dat nebo oboru názvů. Pokud změníte název nebo obor názvů tohoto typu základního kontraktu dat, je potřeba zachovat název kontraktu dat a oboru názvů pomocí příslušné mechanismy, jako <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute>. Další informace o pojmenování naleznete v tématu [názvy datových kontraktů](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  V novějších verzích Neměňte názvy žádné datové členy. Pokud změníte název pole, vlastnost nebo událost základní datový člen, použijte `Name` vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> zachovat existující názvem datového členu.  
  
6.  Neměňte typ pole, vlastnost nebo událost základní datový člen tak, aby výsledná data smlouvy pro tento člen změny dat, v novějších verzích. Uvědomte si, že typy rozhraní jsou ekvivalentní <xref:System.Object> pro účely stanovení smlouvy očekávaná data.  
  
7.  V novějších verzích, neměňte pořadí existující datové členy úpravou <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.  
  
8.  V novějších verzích je možné přidat nové datové členy. By měl vždy postupujte podle těchto pravidel:  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Vlastnost by měl vždy být ponechány na jeho výchozí hodnotu `false`.  
  
    2.  Pokud výchozí hodnotu `null` nebo klesne na nepřijatelnou nulu pro člen, musí být zadaná metoda zpětného volání pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute> zajistit přiměřené výchozí hodnoty v případě, že člen není k dispozici v příchozím datovém proudu. Další informace o zpětné volání, naleznete v tématu [tolerantní zpětná volání serializace](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> Vlastnost by měla sloužit k Ujistěte se, že všichni členové nově přidaná data se zobrazí po existující datové členy. Doporučený způsob, jak to vypadá takto: Žádné datové členy v první verzi kontraktu dat by měl mít jejich `Order` sadu vlastností. Všechny datové členy, které byly přidány ve verzi 2 kontraktu dat by měl mít jejich `Order` nastavenou na 2. Všechny datové členy, které byly přidány ve verzi 3 kontraktu dat by měl mít jejich `Order` nastaven na hodnotu 3 a tak dále. Je přípustné mít více než jeden datový člen nastaví na stejnou `Order` číslo.  
  
9. Neodebírejte datové členy v novějších verzích, i v případě, <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost byla ponechána v její výchozí vlastnost `false` v předchozích verzích.  
  
10. Neměňte `IsRequired` vlastnost na žádné existující datové členy z verze na verzi.  
  
11. Pro požadované datové členy (kde `IsRequired` je `true`), se nezmění `EmitDefaultValue` vlastnost z verze na verzi.  
  
12. Nepokoušejte se vytváření hierarchií větvenou správy verzí. To znamená, že by měla být vždy cestu minimálně jeden směr z libovolné verze na jakoukoli jinou verzi pomocí pouze změny, které jsou povolené podle následujících pokynů.  
  
     Například, pokud verze 1 kontraktu dat osoby obsahuje pouze datový člen název, nevytvářejte 2a verze kontraktu přidávání pouze stáří člen a verze 2b přidávání pouze člena adresy. Budete z 2a 2b by vyžadovalo odebrání stáří a přidání adresy; do toho pustit v opačným směrem by za následek odebrání adres a přidání věk. Odebírají se členové nepovoluje podle následujících pokynů.  
  
13. Obecně nevytvářejte nový podtypy existující typy kontraktů dat v nové verzi vaší aplikace. Podobně nevytvářejte nové kontraktů dat, které se používají místo data, která členy deklarované jako objekt nebo jako typy rozhraní. Vytvoření těchto nových tříd je povoleno pouze v případě, že víte, že můžete přidat nové typy do seznamu známých typů všech instancí vaše staré aplikace v. Ve verzi 1 vaše aplikace může například mít LibraryItem datový typ s knihu kontraktu a novinách data smlouvy podtypy. LibraryItem by pak měl u seznamu známých typů, která obsahuje adresář a novinách. Předpokládejme, že přidáte typ Magazine nyní ve verzi 2, která je podtypem typu LibraryItem. Pokud odešlete instanci Magazine z verze 2 verze 1, časopisu kontraktu dat nebyl nalezen v seznamu známých typů a je vyvolána výjimka.  
  
14. Neměli přidat nebo odebrat členy výčtu mezi verzemi. Členy výčtu, by neměla také přejmenovat, pokud použijete vlastnost Name na `EnumMemberAttribute` atribut zachovat jejich názvy v datovém modelu smlouvy stejné.  
  
15. Kolekce jsou zaměnitelné v datovém modelu smlouvy, jak je popsáno v [typy kolekcí v kontraktech dat](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). To umožňuje vysoký stupeň flexibilitu. Ale ujistěte se, že neměnit neúmyslně typ kolekce ve jiných zaměnitelné verze způsobem. Například neměňte z kolekce neupravené (to znamená bez `CollectionDataContractAttribute` atribut) do přizpůsobené jedné nebo vlastní kolekci pro jeden neupravené. Také, neměňte vlastnosti na `CollectionDataContractAttribute` mezi verzemi. Jediná povolená změna je přidání vlastnosti Name nebo Namespace, pokud došlo ke změně názvu nebo oboru názvů základní typ kolekce a budete muset udělat svá data smlouvy názvem a oborem názvů stejné, jako v předchozí verzi.  
  
 Některé zde uvedené pokyny můžete bezpečně ignorovat při použití zvláštní okolnosti. Ujistěte se, že plně chápete serializace, deserializace a schéma mechanismy upozorněni před odchýlení od pokynů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Použití kontraktů dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Správa verzí kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Názvy kontraktů dat](../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Kontrakty dat s dopřednou kompatibilitou](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Zpětná volání serializace tolerantní k verzím](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
