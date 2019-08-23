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
ms.openlocfilehash: 309cd891fd2d764314060e49a401bd1d8f7b8d32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963257"
---
# <a name="data-contract-versioning"></a>Správa verzí kontraktů dat
V případě vývoje aplikací může být také nutné změnit data kontraktů, které služba používá. Toto téma vysvětluje, jak verze kontraktů dat. Toto téma popisuje mechanismy správy verzí kontraktů dat. Úplný přehled a podrobné pokyny k používání verzí najdete v tématu [osvědčené postupy: Správa verzí](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)kontraktů dat  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Přerušení vs. Nepřerušené změny  
 Změny kontraktu dat můžou být přerušené nebo nepřerušované. Pokud se kontrakt dat změní při nerozdělení, aplikace používající starší verzi smlouvy může komunikovat s aplikací pomocí novější verze a aplikace používající novější verzi kontraktu může komunikovat s aplikací. použití starší verze. Na druhé straně zásadní změna brání v komunikaci v jednom nebo obou směrech.  
  
 Jakékoli změny typu, které neovlivňují způsob přenosu a přijetí, jsou nepřerušené. Tyto změny nemění kontrakt dat pouze ze základního typu. Například můžete změnit název pole při nerozdělování, pokud nastavíte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> na název starší verze. Následující kód ukazuje verzi 1 kontraktu dat.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Následující kód ukazuje nepřerušenou změnu.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Některé změny upraví přenášená data, ale mohou nebo nemusí být přerušují. Následující změny se vždycky přerušují:  
  
- Změna hodnoty <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> nebo kontraktu dat. <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
  
- Změna pořadí datových členů pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnosti. <xref:System.Runtime.Serialization.DataMemberAttribute>  
  
- Přejmenování datového členu.  
  
- Změna kontraktu dat datového členu. Například změna typu datového členu z celého čísla na řetězec nebo z typu s kontraktem dat s názvem "Customer" na typ s kontraktem dat s názvem "Person".  
  
 K dispozici jsou také následující změny.  
  
## <a name="adding-and-removing-data-members"></a>Přidávání a odebírání datových členů  
 Ve většině případů není přidání nebo odebrání datového členu zásadní změnou, pokud nevyžadujete striktní platnost schématu (nové instance ověřování proti starému schématu).  
  
 Když je typ s polem extra deserializovaný na typ s chybějícím polem, další informace se ignorují. (Může být také uloženo pro účely Round-Trip; Další informace najdete v tématu [kontrakty dat kompatibilní s](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)dopředně).  
  
 Když je typ s chybějícím polem deserializovaný na typ s polem extra, pole navíc zůstane na výchozí hodnotě, obvykle nula nebo `null`. (Výchozí hodnota může být změněna. Další informace naleznete v tématu [zpětná volání serializace odolná proti verzi](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Můžete například použít `CarV1` třídu na klientovi `CarV2` a třídu ve službě, `CarV1` nebo můžete použít třídu na službě a `CarV2` třídu na klientovi.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Koncový bod verze 2 může úspěšně odeslat data do koncového bodu verze 1. Serializace verze 2 `Car` kontraktu dat vypočítá XML podobně jako následující.  
  
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
 Datový člen může být označen jako vyžadovaný, nastavením <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> `true`na. Pokud při deserializaci chybějí požadovaná data, je vyvolána výjimka namísto nastavení datového členu na jeho výchozí hodnotu.  
  
 Přidání požadovaného datového členu je zásadní změna. To znamená, že novější typ lze nadále odeslat koncovým bodům se starším typem, ale nikoli jiným způsobem. Odebrání datového členu, který byl označen jako vyžadovaný v jakékoli předchozí verzi, je také zásadní změnou.  
  
 `false` `true` `false` Změna hodnoty `true` vlastnosti z na není vyměněna, ale změna z na je možné přerušit, pokud některé předchozí verze typu nemají daný datový člen. <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
  
> [!NOTE]
> I když je `true` <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost nastavená na, příchozí data můžou mít hodnotu null nebo být nula a typ musí být připravený pro zpracování této možnosti. Nepoužívejte <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako bezpečnostní mechanismus k ochraně před nesprávnými příchozími daty.  
  
## <a name="omitted-default-values"></a>Vynechané výchozí hodnoty  
 Je možné (i když nedoporučujeme) nastavit `EmitDefaultValue` vlastnost u atributu DataMemberAttribute na `false`, jak je popsáno v části [výchozí hodnoty datových členů](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Pokud je `false`toto nastavení, datový člen nebude vygenerován, pokud je nastaven na výchozí hodnotu (obvykle je null nebo nula). Tato možnost není kompatibilní s požadovanými datovými členy v různých verzích dvěma způsoby:  
  
- Kontrakt dat s datovým členem, který je požadován v jedné verzi, nemůže přijmout výchozí hodnoty (null nebo nula) z jiné verze, ve které je datový člen `EmitDefaultValue` nastaven na `false`.  
  
- Požadovaný datový člen, který je `EmitDefaultValue` nastaven na `false` hodnotu nelze použít k serializaci výchozí hodnoty (null nebo nula), ale může získat takovou hodnotu v deserializaci. Tím se vytvoří problém s kulatým Tripem (data se dají číst, ale stejná data se pak nedají zapsat). Proto pokud `IsRequired` je `true` a `EmitDefaultValue` je vjednéverzi,stejnákombinacebysemělavztahovatnavšechnyostatníverze,abyžádnáverzekontraktudatnemohlavytvořithodnotu,kteránemázanásledekzpožděníodezvy.`false`  
  
## <a name="schema-considerations"></a>Otázky schématu  
 Vysvětlení toho, jaké schéma je vytvořeno pro typy kontraktů dat, naleznete v tématu [referenční informace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schéma WCF generuje pro typy kontraktů dat neposkytuje žádné ustanovení pro správu verzí. To znamená, že schéma exportované z určité verze typu obsahuje pouze datové členy, které jsou obsaženy v dané verzi. <xref:System.Runtime.Serialization.IExtensibleDataObject> Implementace rozhraní nemění schéma pro daný typ.  
  
 Datové členy jsou ve výchozím nastavení exportovány do schématu jako nepovinné prvky. To znamená, `minOccurs` že hodnota (XML atribut) je nastavená na 0. Požadované datové členy jsou exportovány `minOccurs` s nastavením na hodnotu 1.  
  
 Mnohé z změn, které se považují za nepřerušované, se ve skutečnosti přerušují, pokud je potřeba striktní dodržování schématu. `CarV1` V předchozím příkladu by instance s `CarV2` `Model` pouze elementem byla ověřena proti schématu (které má obojí `Model` `Horsepower`i, ale obě jsou volitelné). Opačný opak ale neplatí: `CarV2` instance selže při ověřování `CarV1` u schématu.  
  
 Round-Trip také zahrnuje některé další okolnosti. Další informace najdete v části "požadavky na schéma" v [kontraktech dat kompatibilních s podporou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)dopředných.  
  
### <a name="other-permitted-changes"></a>Jiné povolené změny  
 <xref:System.Runtime.Serialization.IExtensibleDataObject> Implementace rozhraní je nepřerušená změna. Podpora s kulatým trip pro verze typu před verzí, ve které <xref:System.Runtime.Serialization.IExtensibleDataObject> byla implementována, však neexistuje. Další informace najdete v tématu [kontrakty dat kompatibilní s](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)dopředné.  
  
## <a name="enumerations"></a>Výčty  
 Přidání nebo odebrání člena výčtu je zásadní změna. Změna názvu člena výčtu je rozbitá, pokud se jeho název kontraktu neudržuje stejně jako ve staré verzi pomocí `EnumMemberAttribute` atributu. Další informace najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekce  
 Většina změn kolekcí je nepřerušovaná, protože většina typů kolekcí je vzájemně zaměnitelné v modelu kontraktu dat. Nicméně změna nepřizpůsobené kolekce je přizpůsobená nebo naopak beze změny. Změna nastavení přizpůsobení kolekce také představuje zásadní změnu. To znamená, že se změní název a obor názvů kontraktu dat, název opakujícího se elementu, název klíčového elementu a název elementu hodnoty. Další informace o přizpůsobení kolekce najdete v tématu [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Přirozeně Změna data kontraktu obsahu kolekce (například změna ze seznamu celých čísel na seznam řetězců) je zásadní změna.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Zpětná volání serializace tolerantní k verzím](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Kontrakty dat s dopřednou kompatibilitou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
