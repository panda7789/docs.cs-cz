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
ms.openlocfilehash: b2bfe253011e24e6792fc60221d05fd60555e87c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627051"
---
# <a name="data-contract-versioning"></a>Správa verzí kontraktů dat
Jak vyvíjet aplikace, budete také muset změnit data smluv týkajících se používání služby. Toto téma vysvětluje, jak kontraktů dat verze. Toto téma popisuje mechanismy správy verzí pomocí kontraktu dat. Úplný přehled a doporučené postupy správy verzí pokyny najdete v tématu [osvědčených postupů: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Zásadní vs. Méně zásadních změn  
 Změny kontraktu dat může být dopadem na dřívější kód nebo pevná. Při změně kontraktu dat pevná způsobem, aplikaci pomocí starší verze kontraktu můžou klienti komunikovat pomocí novější verze aplikace a aplikace pomocí novější verze kontraktu může komunikovat s aplikací pomocí starší verze. Rozbíjející změny na druhé straně znemožňuje komunikaci v jednom či obou směrech.  
  
 Všechny změny na typ, které nemají vliv na tom, jak je odeslaných a přijatých jsou pevné. Tyto změny neměňte kontraktu dat pouze základního typu. Například můžete změnit název pole tak méně zásadních Pokud pak nastavíte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> k názvu starší verze. Následující kód ukazuje verzi 1 služby data smlouvy.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Následující kód ukazuje méně zásadních změn.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Některé změny upravovat přenášená data, ale může nebo nemusí být zásadní. Tyto změny jsou vždy dopadem na dřívější kód:  
  
- Změna <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> nebo <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> hodnota dat kontraktu.  
  
- Změna pořadí datových členů pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
- Datový člen přejmenování.  
  
- Změna kontraktu dat datový člen. Například změna typu datového členu z celého čísla na řetězec, nebo z typu s kontraktem dat s názvem "Customer" na typ s kontraktem dat s názvem "Osoba".  
  
 Tyto změny jsou také je to možné.  
  
## <a name="adding-and-removing-data-members"></a>Přidávání a odebírání datových členů  
 Ve většině případů přidáním nebo odebráním datového členu není rozbíjející změny, pokud vyžadujete striktní schéma platnosti (ověření proti schématu staré nové instance).  
  
 Když do typu s chybějící pole je deserializovat typ se další pole, je ignorován dodatečné informace. (Může být také uložena pro účely verzemi; Další informace, najdete v článku [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Při typu s chybějící pole je deserializovat na typ s další pole, pole navíc je ponecháno na výchozí hodnotě, obvykle nula nebo `null`. (Výchozí hodnota může být změněn; Další informace najdete v tématu [tolerantní zpětná volání serializace](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Například můžete použít `CarV1` třídy v klientském počítači a `CarV2` třídy na službu, nebo můžete použít `CarV1` třídy ve službě a `CarV2` třídy v klientském počítači.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Koncový bod verze 2 můžete úspěšně odeslat data na koncový bod verze 1. Serializaci verze 2 `Car` kontraktu dat vrací XML podobný následujícímu.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Deserializace modulu ve V1 nelze najít odpovídající datový člen pro `HorsePower` pole a zahodí tato data.  
  
 Koncový bod verze 1 může také odesílat data na koncový bod verze 2. Serializaci verze 1 `Car` kontraktu dat vrací XML podobný následujícímu.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Verze 2 deserializátor nezná co mají nastavit `HorsePower` pole, protože neexistuje žádná odpovídající data v příchozích XML. Místo toho pole je nastaveno na výchozí hodnotu 0.  
  
## <a name="required-data-members"></a>Požadované datové členy  
 Datový člen může být označena jako požadovaným nastavením <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> k `true`. Pokud je to nutné, že data budou chybějící při deserializaci, je vyvolána výjimka místo nastavení na výchozí hodnotu datový člen.  
  
 Přidání požadovaný datový člen je zásadní změnu. To znamená novější typ je stále možné odeslat do koncových bodů s starší typu, ale ne naopak. Odebrání datový člen, který byl označen jako v jakékoli předchozí verze je také k zásadní změně.  
  
 Změna <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> hodnota vlastnosti z `true` k `false` není zásadní, ale změna ze `false` k `true` může být rozdělení všechny předchozí verze typu nemají datový člen dotyčný.  
  
> [!NOTE]
>  I když <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> je nastavena na `true`, příchozích dat může mít hodnotu null nebo nula a typ musí být připravena ke zpracování této možnosti. Nepoužívejte <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako vhodný mechanismus zabezpečení pro ochranu před chybná příchozí data.  
  
## <a name="omitted-default-values"></a>Vynechaný výchozí hodnoty  
 Je možné (ale nedoporučuje se) Chcete-li nastavit `EmitDefaultValue` vlastnost u atributu DataMemberAttribute `false`, jak je popsáno v [výchozí hodnoty datových členů](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Pokud je toto nastavení `false`, nebude se emitovat datový člen, pokud je nastavena na výchozí hodnotu (obvykle nebo má nulovou hodnotu). Toto není kompatibilní s požadované datové členy v různých verzích dvěma způsoby:  
  
- Kontrakt dat s datovým členem, který je vyžadován v jedné verzi nemůže přijmout výchozí (nebo má nulovou hodnotu) dat z jiné verze, ve kterém má datový člen `EmitDefaultValue` nastavena na `false`.  
  
- Povinný datový člen, který má `EmitDefaultValue` nastavena na `false` nelze použít k serializaci jeho výchozí (nebo má nulovou hodnotu), hodnotu, ale mohou přijímat taková hodnota k deserializaci. Vzniká tak problém verzemi (lze číst data v ale stejná data nelze poté zapíšou). Proto pokud `IsRequired` je `true` a `EmitDefaultValue` je `false` v jedné verzi stejnou kombinaci by se měly používat pro všechny ostatní verze tak, aby žádná verze kontraktu dat mohl by být schopen vytvořit hodnotu, která nemá za následek odezvy.  
  
## <a name="schema-considerations"></a>Schema Considerations  
 Vysvětlení, jaké schéma je vytvořen pro typy kontraktů dat, najdete v článku [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schéma WCF vytváří pro typy kontraktů dat znamená žádné ustanovení pro správu verzí. To znamená schéma exportované z verzi typu obsahuje pouze tyto datové členy v této verzi k dispozici. Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní nedojde ke změně schématu typu.  
  
 Datové členy se vyexportují do schématu jako volitelné elementy ve výchozím nastavení. To znamená `minOccurs` hodnoty (atribut XML) je nastavena na hodnotu 0. Požadované datové členy se vyexportují se `minOccurs` nastavena na hodnotu 1.  
  
 Mnoho změn považuje za pevná jsou ve skutečnosti přerušení, pokud se vyžaduje striktní dodržování schématu. V předchozím příkladu `CarV1` instanci s jenom `Model` element bude ověřovat proti `CarV2` schématu (který má obě `Model` a `Horsepower`, ale oba jsou volitelné). Ale, opak není pravdou: `CarV2` instance selže ověření proti `CarV1` schématu.  
  
 Verzemi zahrnuje také několik dalších důležitých informací. Další informace najdete v části "Požadavky schématu" v [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Ostatní povolené změny  
 Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní je méně zásadních změn. Ale verzemi podporu neexistuje pro verze starší než verze, ve kterém typu <xref:System.Runtime.Serialization.IExtensibleDataObject> bylo implementováno. Další informace najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Výčty  
 Přidání nebo odebrání člen výčtového typu je zásadní změnu. Mění se název na člena výčtu je zásadní, pokud jeho název kontraktu zůstane stejná jako v předchozí verzi aplikace s použitím `EnumMemberAttribute` atribut. Další informace najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekce  
 Většina změn kolekce jsou pevné protože většinu typů kolekcí jsou zaměnitelné mezi sebou v datovém modelu kontraktu. Ale vytváření noncustomized kolekci přizpůsobili nebo naopak je zásadní změnu. Změna nastavení přizpůsobení kolekce je také k zásadní změně; To znamená změně jeho názvem kontraktu dat a obor názvů, opakující se název elementu, klíčovým prvkem název a hodnotu názvu elementu. Další informace o shromažďování vlastního nastavení naleznete v tématu [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Přirozeně změna kontraktu dat kolekce (například změna ze seznamu celých čísel do seznam řetězců) obsah je zásadní změnu.  
  
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
