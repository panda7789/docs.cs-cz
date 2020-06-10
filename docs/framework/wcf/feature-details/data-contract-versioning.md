---
title: Správa verzí kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 493efab41e2c6763eb95df8662e6254d9e0df2f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593500"
---
# <a name="data-contract-versioning"></a>Správa verzí kontraktů dat
V případě vývoje aplikací může být také nutné změnit data kontraktů, které služba používá. Toto téma vysvětluje, jak verze kontraktů dat. Toto téma popisuje mechanismy správy verzí kontraktů dat. Úplný přehled a podrobné pokyny k používání verzí najdete v tématu [osvědčené postupy: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Přerušení vs. nepřerušené změny  
 Změny kontraktu dat můžou být přerušené nebo nepřerušované. Pokud se kontrakt dat změní v nerozdělování, aplikace používající starší verzi smlouvy může komunikovat s aplikací pomocí novější verze a aplikace používající novější verzi kontraktu může komunikovat s aplikací pomocí starší verze. Na druhé straně zásadní změna brání v komunikaci v jednom nebo obou směrech.  
  
 Jakékoli změny typu, které neovlivňují způsob přenosu a přijetí, jsou nepřerušené. Tyto změny nemění kontrakt dat pouze ze základního typu. Například můžete změnit název pole při nerozdělování, pokud nastavíte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost na <xref:System.Runtime.Serialization.DataMemberAttribute> název starší verze. Následující kód ukazuje verzi 1 kontraktu dat.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Následující kód ukazuje nepřerušenou změnu.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Některé změny upraví přenášená data, ale mohou nebo nemusí být přerušují. Následující změny se vždycky přerušují:  
  
- Změna <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> hodnoty nebo <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> kontraktu dat.  
  
- Změna pořadí datových členů pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
- Přejmenování datového členu.  
  
- Změna kontraktu dat datového členu. Například změna typu datového členu z celého čísla na řetězec nebo z typu s kontraktem dat s názvem "Customer" na typ s kontraktem dat s názvem "Person".  
  
 K dispozici jsou také následující změny.  
  
## <a name="adding-and-removing-data-members"></a>Přidávání a odebírání datových členů  
 Ve většině případů není přidání nebo odebrání datového členu zásadní změnou, pokud nevyžadujete striktní platnost schématu (nové instance ověřování proti starému schématu).  
  
 Když je typ s polem extra deserializovaný na typ s chybějícím polem, další informace se ignorují. (Může být také uloženo pro účely Round-Trip; Další informace najdete v tématu [kontrakty dat kompatibilní s dopředně](forward-compatible-data-contracts.md)).  
  
 Když je typ s chybějícím polem deserializovaný na typ s polem extra, pole navíc zůstane na výchozí hodnotě, obvykle nula nebo `null` . (Výchozí hodnota může být změněna. Další informace naleznete v tématu [zpětná volání serializace odolná proti verzi](version-tolerant-serialization-callbacks.md).)  
  
 Můžete například použít `CarV1` třídu na klientovi a `CarV2` třídu ve službě, nebo můžete použít `CarV1` třídu na službě a `CarV2` třídu na klientovi.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Koncový bod verze 2 může úspěšně odeslat data do koncového bodu verze 1. Serializace verze 2 `Car` kontraktu dat VYPOČÍTÁ XML podobně jako následující.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Modul deserializace v v1 nenalezne odpovídající datový člen pro `HorsePower` pole a zahodí tato data.  
  
 Koncový bod verze 1 také může odesílat data do koncového bodu verze 2. Serializace verze 1 `Car` kontraktu dat poskytuje jazyk XML podobný následujícímu.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Deserializátor verze 2 neví, co nastavit `HorsePower` pole na, protože v příchozích XML nejsou žádná data, která by odpovídala. Místo toho je pole nastaveno na výchozí hodnotu 0.  
  
## <a name="required-data-members"></a>Požadované datové členy  
 Datový člen může být označen jako vyžadovaný, nastavením <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnosti na <xref:System.Runtime.Serialization.DataMemberAttribute> `true` . Pokud při deserializaci chybějí požadovaná data, je vyvolána výjimka namísto nastavení datového členu na jeho výchozí hodnotu.  
  
 Přidání požadovaného datového členu je zásadní změna. To znamená, že novější typ lze nadále odeslat koncovým bodům se starším typem, ale nikoli jiným způsobem. Odebrání datového členu, který byl označen jako vyžadovaný v jakékoli předchozí verzi, je také zásadní změnou.  
  
 Změna <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> hodnoty vlastnosti z na není vyměněna `true` `false` , ale změna z `false` na je `true` možné přerušit, pokud některé předchozí verze typu nemají daný datový člen.  
  
> [!NOTE]
> I když <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> je vlastnost nastavená na `true` , příchozí data můžou mít hodnotu null nebo být nula a typ musí být připravený pro zpracování této možnosti. Nepoužívejte <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako bezpečnostní mechanismus k ochraně před nesprávnými příchozími daty.  
  
## <a name="omitted-default-values"></a>Vynechané výchozí hodnoty  
 Je možné (i když nedoporučujeme) nastavit `EmitDefaultValue` vlastnost u atributu DataMemberAttribute na `false` , jak je popsáno v části [výchozí hodnoty datových členů](data-member-default-values.md). Pokud je toto nastavení `false` , datový člen nebude vygenerován, pokud je nastaven na výchozí hodnotu (obvykle je null nebo nula). Tato možnost není kompatibilní s požadovanými datovými členy v různých verzích dvěma způsoby:  
  
- Kontrakt dat s datovým členem, který je požadován v jedné verzi, nemůže přijmout výchozí hodnoty (null nebo nula) z jiné verze, ve které je datový člen `EmitDefaultValue` nastaven na `false` .  
  
- Požadovaný datový člen, který je `EmitDefaultValue` nastaven na `false` hodnotu nelze použít k serializaci výchozí hodnoty (null nebo nula), ale může získat takovou hodnotu v deserializaci. Tím se vytvoří problém s kulatým Tripem (data se dají číst, ale stejná data se pak nedají zapsat). Proto pokud `IsRequired` je `true` a `EmitDefaultValue` je `false` v jedné verzi, stejná kombinace by se měla vztahovat na všechny ostatní verze, aby žádná verze kontraktu dat nemohla vytvořit hodnotu, která nemá za následek zpoždění odezvy.  
  
## <a name="schema-considerations"></a>Otázky schématu  
 Vysvětlení toho, jaké schéma je vytvořeno pro typy kontraktů dat, naleznete v tématu [referenční informace schématu kontraktu dat](data-contract-schema-reference.md).  
  
 Schéma WCF generuje pro typy kontraktů dat neposkytuje žádné ustanovení pro správu verzí. To znamená, že schéma exportované z určité verze typu obsahuje pouze datové členy, které jsou obsaženy v dané verzi. Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní nemění schéma pro daný typ.  
  
 Datové členy jsou ve výchozím nastavení exportovány do schématu jako nepovinné prvky. To znamená, že `minOccurs` hodnota (XML atribut) je nastavená na 0. Požadované datové členy jsou exportovány s `minOccurs` nastavením na hodnotu 1.  
  
 Mnohé z změn, které se považují za nepřerušované, se ve skutečnosti přerušují, pokud je potřeba striktní dodržování schématu. V předchozím příkladu `CarV1` by instance s pouze `Model` elementem byla ověřena proti `CarV2` schématu (které má obojí i `Model` `Horsepower` , ale obě jsou volitelné). Opačný opak ale neplatí: `CarV2` instance selže při ověřování u `CarV1` schématu.  
  
 Round-Trip také zahrnuje některé další okolnosti. Další informace najdete v části "požadavky na schéma" v [kontraktech dat kompatibilních s podporou dopředných](forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Jiné povolené změny  
 Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní je nepřerušená změna. Podpora s kulatým trip pro verze typu před verzí, ve které <xref:System.Runtime.Serialization.IExtensibleDataObject> byla implementována, však neexistuje. Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Výčty  
 Přidání nebo odebrání člena výčtu je zásadní změna. Změna názvu člena výčtu je rozbitá, pokud se jeho název kontraktu neudržuje stejně jako ve staré verzi pomocí `EnumMemberAttribute` atributu. Další informace najdete v tématu [výčtové typy v kontraktech dat](enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekce  
 Většina změn kolekcí je nepřerušovaná, protože většina typů kolekcí je vzájemně zaměnitelné v modelu kontraktu dat. Nicméně změna nepřizpůsobené kolekce je přizpůsobená nebo naopak beze změny. Změna nastavení přizpůsobení kolekce také představuje zásadní změnu. To znamená, že se změní název a obor názvů kontraktu dat, název opakujícího se elementu, název klíčového elementu a název elementu hodnoty. Další informace o přizpůsobení kolekce najdete v tématu [typy kolekcí v kontraktech dat](collection-types-in-data-contracts.md).  
Přirozeně Změna data kontraktu obsahu kolekce (například změna ze seznamu celých čísel na seznam řetězců) je zásadní změna.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Zpětná volání serializace tolerantní k verzím](version-tolerant-serialization-callbacks.md)
- [Osvědčené postupy: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md)
- [Použití kontraktů dat](using-data-contracts.md)
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Kontrakty dat s dopřednou kompatibilitou](forward-compatible-data-contracts.md)
