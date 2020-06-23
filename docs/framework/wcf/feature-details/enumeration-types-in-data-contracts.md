---
title: Výčtové typy v kontraktech dat
description: Přečtěte si, jak model kontraktu dat vyjadřuje výčty jako součást programovacího modelu WFC.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: ff3184a285e88d47d4545a38a6c74b2f209827fb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247296"
---
# <a name="enumeration-types-in-data-contracts"></a>Výčtové typy v kontraktech dat
Výčty lze vyjádřit v modelu kontraktu dat. Toto téma vás provede několika příklady, které vysvětlují programovací model.  
  
## <a name="enumeration-basics"></a>Základy výčtu  
 Jedním ze způsobů, jak používat výčtové typy v modelu kontraktu dat, je použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ. Pak je nutné použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut pro každého člena, který musí být zahrnut v kontraktu dat.  
  
 Následující příklad ukazuje dvě třídy. První používá výčet a druhý definuje výčet.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Instanci `Car` třídy lze odeslat nebo přijmout pouze v případě `condition` , že je pole nastaveno na jednu z hodnot `New` , `Used` nebo `Rental` . Pokud `condition` je `Broken` nebo `Stolen` , a <xref:System.Runtime.Serialization.SerializationException> je vyvolána.  
  
 <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> Pro kontrakty dat výčtu můžete použít vlastnosti (a) obvyklým způsobem.  
  
### <a name="enumeration-member-values"></a>Hodnoty členů výčtu  
 Obecně platí, že kontrakt dat zahrnuje názvy členů výčtu, nikoli číselné hodnoty. Při použití modelu kontraktu dat je však v případě, že je přijímající strana klientem služby WCF, vyexportované schéma zachovává číselné hodnoty. Všimněte si, že se nejedná o případ použití [třídy XmlSerializer](using-the-xmlserializer-class.md).  
  
 Pokud je v předchozím příkladu `condition` nastaveno na `Used` a data jsou serializována do formátu XML, výsledný kód XML je `<condition>Used</condition>` a nikoli `<condition>1</condition>` . Následující kontrakt dat je proto rovnocenný kontraktu dat `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Můžete například použít `CarConditionEnum` na straně odeslání a `CarConditionWithNumbers` na straně příjmu. I když odesílající strana používá hodnotu "1" pro `Used` a na straně příjmu se používá hodnota "20", reprezentace XML je určena `<condition>Used</condition>` pro obě strany.  
  
 Aby bylo možné zahrnout do kontraktu dat, je nutné použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. V .NET Framework můžete vždy použít speciální hodnotu 0 (nula) na výčet, což je také výchozí hodnota pro jakýkoliv výčet. Nicméně i tato speciální nulová hodnota nemůže být serializována, pokud není označena <xref:System.Runtime.Serialization.EnumMemberAttribute> atributem.  
  
 Existují dvě výjimky:  
  
- Výčty příznaků (popsány dále v tomto tématu).  
  
- Vyčíslení datových členů s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastností nastavenou na `false` (v takovém případě je výčet s hodnotou nula vynechán ze serializovaných dat).  
  
### <a name="customizing-enumeration-member-values"></a>Přizpůsobení hodnot členů výčtu  
 Můžete přizpůsobit hodnotu člena výčtu, která tvoří součást kontraktu dat pomocí <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> vlastnosti <xref:System.Runtime.Serialization.EnumMemberAttribute> atributu.  
  
 Například následující kontrakt dat je také ekvivalentní kontraktu dat v `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Při serializaci hodnota `PreviouslyOwned` má reprezentaci XML `<condition>Used</condition>` .  
  
## <a name="simple-enumerations"></a>Jednoduché výčty  
 Můžete také serializovat výčtové typy, na které nebyl <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit. Tyto typy výčtu jsou ošetřeny přesně tak, jak je popsáno, s tím rozdílem, že každý člen (který nemá <xref:System.NonSerializedAttribute> použit atribut) je považován za, pokud byl <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut použit. Například následující výčet má implicitně stejný kontrakt dat jako v předchozím `CarConditionEnum` příkladu.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Jednoduché výčty můžete použít, pokud nepotřebujete přizpůsobit název kontraktu dat výčtu a obor názvů a hodnoty členů výčtu.  
  
#### <a name="notes-on-simple-enumerations"></a>Poznámky k jednoduchým Výčtům  
 Použití <xref:System.Runtime.Serialization.EnumMemberAttribute> atributu na jednoduché výčty nemá žádný vliv.  
  
 Neposkytuje žádný rozdíl bez ohledu na to, zda <xref:System.SerializableAttribute> je atribut použit pro výčet.  
  
 Fakt, že <xref:System.Runtime.Serialization.DataContractSerializer> Třída respektuje <xref:System.NonSerializedAttribute> atribut používaný pro členy výčtu, se liší od chování <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Oba tyto serializátory ignorují <xref:System.NonSerializedAttribute> atribut.  
  
## <a name="flag-enumerations"></a>Označit výčty  
 Atribut lze použít <xref:System.FlagsAttribute> pro výčty. V takovém případě je možné současně odeslat nebo přijmout seznam nulových nebo více hodnot výčtu.  
  
 Uděláte to tak, že použijete <xref:System.Runtime.Serialization.DataContractAttribute> atribut na výčet příznaků a pak označíte všechny členy, kteří jsou mocninami dvou s <xref:System.Runtime.Serialization.EnumMemberAttribute> atributem. Všimněte si, že pokud chcete použít výčet příznaků, průběh musí být nepřerušovaná sekvence mocnin 2 (například 1, 2, 4, 8, 16, 32, 64).  
  
 Následující postup platí pro odeslání hodnoty výčtu příznakem:  
  
1. Došlo k pokusu o nalezení člena výčtu (s <xref:System.Runtime.Serialization.EnumMemberAttribute> použitým atributem), který je namapován na číselnou hodnotu. Když se najde, pošle seznam, který obsahuje jenom tohoto člena.  
  
2. Pokusí se rozdělit číselnou hodnotu na součet tak, aby existovaly členy výčtu (každý s <xref:System.Runtime.Serialization.EnumMemberAttribute> atributem použit), které jsou mapovány na každou část součtu. Odešle seznam všech těchto členů. Všimněte si, že *algoritmus hladce* se používá k vyhledání takového součtu, a proto není nijak zaručeno, že se tato suma najde, i když je k dispozici. Chcete-li se tomuto problému vyhnout, ujistěte se, že číselné hodnoty členů výčtu mají dvě mocniny.  
  
3. Pokud předchozí dva kroky selžou a číselná hodnota je nenulová, vyvolejte a <xref:System.Runtime.Serialization.SerializationException> . Pokud je číselná hodnota nula, odešlete prázdný seznam.  
  
### <a name="example"></a>Příklad  
 Následující příklad výčtu lze použít v operaci Flag.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Následující příklady hodnot jsou serializovány, jak je uvedeno.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Použití kontraktů dat](using-data-contracts.md)
- [Určování přenosu dat v kontraktech služby](specifying-data-transfer-in-service-contracts.md)
