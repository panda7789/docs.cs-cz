---
title: 'Osvědčené postupy: Správa verzí kontraktů dat'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 4d500c37efa4a90e24b06cd2e886147e1f159d4e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320782"
---
# <a name="best-practices-data-contract-versioning"></a>Osvědčené postupy: Správa verzí kontraktů dat
Toto téma obsahuje seznam osvědčených postupů pro vytváření kontraktů dat, které se můžou v průběhu času vyvíjet snadno. Další informace o kontraktech dat najdete v tématech v tématu [Použití kontraktů dat](./feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Poznámka při ověřování schématu  
 V diskuzi o verzích kontraktů dat je důležité si uvědomit, že schéma kontraktu dat exportovaného službou Windows Communication Foundation (WCF) nemá žádnou podporu správy verzí, kromě faktu, že ve výchozím nastavení jsou prvky označeny jako volitelné.  
  
 To znamená, že dokonce i Nejběžnější scénář správy verzí, jako je například přidání nového datového člena, nelze implementovat způsobem, který je bez problémů s ohledem na dané schéma. Novější verze kontraktu dat (například s novým datovým členem) neověřují pomocí starého schématu.  
  
 Existuje však mnoho scénářů, ve kterých není vyžadováno striktní dodržování schématu. Mnoho platforem webové služby, včetně webových služeb WCF a XML vytvořených pomocí ASP.NET, neprovádí ve výchozím nastavení ověřování schématu a proto tolerovat nadbytečné prvky, které nejsou popsány ve schématu. Při práci s těmito platformami je snazší implementovat řadu scénářů správy verzí.  
  
 Proto existují dvě sady pokynů pro správu verzí kontraktů dat: jedna sada pro scénáře, kdy je důležitá striktní platnost schématu, a další sada pro scénáře, pokud není.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Správa verzí při vyžadování ověření schématu  
 Pokud je potřeba striktní platnost schématu pro všechny směry (nové – staré a staré až nové), kontrakty dat by se měly považovat za neměnné. Pokud je vyžadována Správa verzí, je třeba vytvořit nový kontrakt dat s jiným názvem nebo oborem názvů a kontrakt služby používající datový typ by měl mít odpovídající verzi.  
  
 Například kontrakt služby pro zpracování nákupních objednávek s názvem `PoProcessing` s operací `PostPurchaseOrder` přebírá parametr, který odpovídá kontraktu dat `PurchaseOrder`. Pokud se má smlouva `PurchaseOrder` změnit, je nutné vytvořit novou kontrakt dat, tj. `PurchaseOrder2`, který obsahuje změny. Pak je nutné zpracovat verzi na úrovni smlouvy služby. Například vytvořením operace `PostPurchaseOrder2`, která převezme parametr `PurchaseOrder2`, nebo vytvořením kontraktu služby `PoProcessing2`, kde operace `PostPurchaseOrder` převezme kontrakt dat `PurchaseOrder2`.  
  
 Všimněte si, že změny v kontraktech dat, na které odkazují jiné datové kontrakty, se také zvyšují na vrstvu modelu služby. Například v předchozím scénáři se kontrakt dat `PurchaseOrder` nemusí měnit. Obsahuje však datový člen kontraktu dat `Customer`, který zase obsahuje datový člen kontraktu dat `Address`, který je třeba změnit. V takovém případě byste museli vytvořit kontrakt dat `Address2` s požadovanými změnami, kontraktem dat `Customer2`, který obsahuje datový člen `Address2`, a kontrakt dat `PurchaseOrder2`, který obsahuje datový člen `Customer2`. Stejně jako v předchozím případě musí být kontrakt služby také ve verzi.  
  
 I když v těchto příkladech se názvy změnily (připojením "2"), doporučuje se změnit obory názvů místo názvů připojením nových oborů názvů s číslem verze nebo datem. Například kontrakt dat `http://schemas.contoso.com/2005/05/21/PurchaseOrder` se změní na kontrakt dat `http://schemas.contoso.com/2005/10/14/PurchaseOrder`.  
  
 Další informace najdete v tématu osvědčené postupy: [Správa verzí služeb](service-versioning.md).  
  
 V některých případech je potřeba zajistit striktní dodržování předpisů schématu pro zprávy odesílané vaší aplikací, ale nemůžou spoléhat na to, že příchozí zprávy budou odpovídat striktnímu schématu. V takovém případě existuje nebezpečí, že příchozí zpráva může obsahovat nadbytečné údaje. Nadbytečné hodnoty jsou uloženy a vraceny službou WCF, takže mají za následek odeslání neplatných zpráv. Chcete-li se tomuto problému vyhnout, měla by být vypnuta funkce Round-Trip. To můžete provést dvěma způsoby.  
  
- Neimplementujte rozhraní <xref:System.Runtime.Serialization.IExtensibleDataObject> na žádném z vašich typů.  
  
- Použijte atribut <xref:System.ServiceModel.ServiceBehaviorAttribute> u kontraktu služby s vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> nastavenou na `true`.  
  
 Další informace o kulatých Trip najdete v článku [kontrakty dat kompatibilní s dopředně](./feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Správa verzí, když není vyžadováno ověření schématu  
 Striktní kompatibilita schématu je vyžadována zřídka. Řada platforem připustila navíc prvky, které nejsou popsány ve schématu. Pokud je tato možnost tolerována, je možné použít úplnou sadu funkcí popsaných v tématu [Správa verzí kontraktů dat](./feature-details/data-contract-versioning.md) a [kontraktů dat kompatibilních s přesměrováním](./feature-details/forward-compatible-data-contracts.md) . Doporučuje se postupovat podle následujících pokynů.  
  
 Některé pokyny musí být následovány přesně za účelem odeslání nových verzí typu, kde je očekávána starší verze, nebo pro odeslání staré, kde se očekává nový. Jiné pokyny nejsou bezpodmínečně nutné, ale jsou tady uvedené, protože můžou být ovlivněné budoucí správou verzí schématu.  
  
1. Neprovádějte pokus o verzi kontraktů dat podle typu dědičnosti. Chcete-li vytvořit novější verze, buď změňte kontrakt dat na existujícím typu, nebo vytvořte nový nesouvisející typ.  
  
2. Použití dědičnosti spolu s kontrakty dat je povoleno za předpokladu, že se dědičnost nepoužívá jako mechanismus správy verzí a že jsou dodržována určitá pravidla. Pokud typ je odvozen z určitého základního typu, neprovádějte jeho odvození od jiného základního typu v budoucí verzi (pokud nemá stejný kontrakt dat). K této výjimce existuje jedna výjimka: typ lze vložit do hierarchie mezi typem kontraktu dat a jeho základním typem, ale pouze v případě, že neobsahuje datové členy se stejnými názvy jako ostatní členové v jakékoli možné verzi ostatních typů v hierarchii. Obecně platí, že použití datových členů se stejnými názvy na různých úrovních stejné hierarchie dědičnosti může vést k vážným problémům se správou verzí a je třeba se jim vyhnout.  
  
3. Od první verze kontraktu dat vždy implementujte <xref:System.Runtime.Serialization.IExtensibleDataObject>, aby se aktivovala kulatá Trip. Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](./feature-details/forward-compatible-data-contracts.md). Pokud jste vydali jednu nebo více verzí typu bez implementace tohoto rozhraní, implementujte ho v další verzi tohoto typu.  
  
4. V novějších verzích neměňte název kontraktu dat ani obor názvů. Pokud měníte název nebo obor názvů typu, který je základem kontraktu dat, nezapomeňte zachovat název kontraktu dat a obor názvů pomocí příslušných mechanismů, jako je například vlastnost <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute>. Další informace o pojmenování najdete v tématu [názvy kontraktů dat](./feature-details/data-contract-names.md).  
  
5. V novějších verzích Neměňte názvy žádných datových členů. Pokud se změní název pole, vlastnosti nebo události podkladového datového členu, použijte vlastnost `Name` <xref:System.Runtime.Serialization.DataMemberAttribute> k zachování existujícího názvu datového členu.  
  
6. V novějších verzích neměňte typ žádného pole, vlastnosti nebo události podkladového datového členu tak, aby se projevil výsledný kontrakt dat pro tento datový člen. Mějte na paměti, že typy rozhraní jsou ekvivalentní <xref:System.Object> pro účely určení očekávaného kontraktu dat.  
  
7. V novějších verzích neměňte pořadí existujících datových členů úpravou vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> atributu <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
8. V novějších verzích lze přidat nové datové členy. Mají vždycky dodržovat tato pravidla:  
  
    1. Vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> by měla vždy zůstat na výchozí hodnotě `false`.  
  
    2. Pokud výchozí hodnota `null` nebo nula pro člena nesouhlasí, je třeba zadat metodu zpětného volání pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute> k poskytnutí přiměřené výchozí hodnoty pro případ, že člen není přítomen v příchozím datovém proudu. Další informace o zpětném volání naleznete v tématu [zpětná volání serializace odolná proti verzi](./feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. Vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> by se měla použít k ujištění, že se všechny nově přidané datové členy zobrazí po stávajících datových členech. Doporučený postup je následující: žádný z datových členů v první verzi kontraktu dat by neměl mít nastavenou vlastnost `Order`. U všech datových členů přidaných ve verzi 2 kontraktu dat by měla být vlastnost `Order` nastavená na hodnotu 2. U všech datových členů přidaných ve verzi 3 kontraktu dat by měla být `Order` nastavená na 3 atd. Je povoleno mít více než jeden datový člen nastavený na stejné číslo `Order`.  
  
9. Neodstraňujte datové členy v novějších verzích, a to ani v případě, že vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> zůstala ve své výchozí vlastnosti `false` v předchozích verzích.  
  
10. Neměňte vlastnost `IsRequired` u všech existujících datových členů z verze na verzi.  
  
11. Pro požadované datové členy (kde `IsRequired` je `true`) neměňte vlastnost `EmitDefaultValue` z verze na verzi.  
  
12. Nepokoušejte se vytvářet větve s více verzemi. To znamená, že by vždy měla být cesta alespoň v jednom směru od libovolné verze k jakékoli jiné verzi, a to pouze pomocí změn povolených těmito pokyny.  
  
     Například pokud verze 1 kontraktu dat osoby obsahuje pouze název datového členu, neměli byste vytvořit verzi 2a smlouvy, která přidává pouze člena věk a verze 2b přidávají pouze člena adresy. Výsledkem z 2a na 2b by bylo odebrání stáří a přidání adresy; ve druhém směru by to vedlo k odebrání adres a přidání stáří. Odebrání členů není v těchto pokynech povoleno.  
  
13. Obecně byste neměli vytvářet nové podtypy stávajících typů kontraktů dat v nové verzi aplikace. Podobně byste neměli vytvářet nové kontrakty dat, které se používají místo datových členů deklarovaných jako objekty nebo jako typy rozhraní. Vytváření těchto nových tříd je povoleno pouze v případě, že víte, že můžete přidat nové typy do seznamu známých typů všech instancí staré aplikace. Například ve verzi 1 vaší aplikace můžete mít typ kontraktu dat LibraryItem s údaji o knize a podtypu kontraktu dat novinek. LibraryItem by pak měl seznam známých typů, který obsahuje knihu a novinku. Předpokládejme, že jste teď přidali typ časopisu ve verzi 2, který je podtypem LibraryItem. Pokud odešlete instanci časopisu z verze 2 na verzi 1, kontrakt dat časopisu se v seznamu známých typů nenalezne a vyvolá se výjimka.  
  
14. Nemusíte přidávat ani odebírat členy výčtu mezi verzemi. Členy výčtu byste také neměli přejmenovat, pokud nepoužijete vlastnost Name v atributu `EnumMemberAttribute`, abyste zachovali jejich názvy v modelu kontraktu dat.  
  
15. Kolekce jsou v modelu kontraktů dat zaměnitelné, jak je popsáno v tématu [typy kolekcí v kontraktech dat](./feature-details/collection-types-in-data-contracts.md). To vám umožní skvělou míru flexibility. Ujistěte se však, že nechtěně nemůžete změnit typ kolekce z verze na verzi bez možnosti změny. Neměňte například z nepřizpůsobené kolekce (to znamená bez atributu `CollectionDataContractAttribute`) na vlastní přizpůsobenou kolekci nebo přizpůsobenou kolekci na nepřizpůsobenou. Neměňte také vlastnosti `CollectionDataContractAttribute` z verze na verzi. Jedinou povolenou změnou je přidání vlastnosti Name nebo Namespace, pokud došlo ke změně názvu nebo oboru názvů základní kolekce typu kolekce a je třeba zadat název kontraktu dat a obor názvů stejně jako v předchozí verzi.  
  
 Některé z uvedených pokynů se můžou bezpečně ignorovat, když se uplatní zvláštní okolnosti. Ujistěte se, že plně rozumíte mechanismům serializace, deserializace a schématu, které se týkají, než se odchylují od pokynů.  
  
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
- [Použití kontraktů dat](./feature-details/using-data-contracts.md)
- [Správa verzí kontraktů dat](./feature-details/data-contract-versioning.md)
- [Názvy kontraktů dat](./feature-details/data-contract-names.md)
- [Kontrakty dat s dopřednou kompatibilitou](./feature-details/forward-compatible-data-contracts.md)
- [Zpětná volání serializace tolerantní k verzím](./feature-details/version-tolerant-serialization-callbacks.md)
