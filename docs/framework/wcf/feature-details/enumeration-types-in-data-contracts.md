---
title: Výčtové typy v kontraktech dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 21f1f948e0bcd088cbe14316760708e10285124b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649307"
---
# <a name="enumeration-types-in-data-contracts"></a>Výčtové typy v kontraktech dat
Výčty lze vyjádřit v datovém modelu kontraktu. Toto téma vás provede několik příkladů, které popisují programovací model.  
  
## <a name="enumeration-basics"></a>Základní informace o výčet  
 Jeden ze způsobů použití výčtové typy v datovém modelu smlouvy je použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut typu. Musíte použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut pro každého člena, který musí být součástí kontraktu dat.  
  
 Následující příklad ukazuje dvě třídy. První způsob využívá výčtu a druhá definuje výčet.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Instance `Car` třídy můžete odeslat ani přijmout jenom v případě `condition` pole nastavena na jednu z hodnot `New`, `Used`, nebo `Rental`. Pokud `condition` je `Broken` nebo `Stolen`, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.  
  
 Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> vlastnosti (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> a <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) jako obvykle pro kontrakty dat výčtu.  
  
### <a name="enumeration-member-values"></a>Hodnoty členů výčtu  
 Kontrakt dat obvykle zahrnuje názvy členů výčtu, nikoli číselné hodnoty. Ale při použití modelu kontraktu dat, pokud je na přijímající straně klienta WCF, zachová exportované schématu číselné hodnoty. Všimněte si, že tomu tak není při použití [horizontálních oddílů pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 V předchozím příkladu Pokud `condition` je nastavena na `Used` a serializuje data XML, je výsledný XML `<condition>Used</condition>` a ne `<condition>1</condition>`. Proto následující kontraktu dat odpovídá kontraktu dat `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Například můžete použít `CarConditionEnum` na straně odesílání a `CarConditionWithNumbers` na straně příjmu. I když na odesílající straně používá hodnotu "1" pro `Used` a přijímající straně používá, je hodnota "20" reprezentaci XML pro `<condition>Used</condition>` pro obě strany.  
  
 Chcete-li být součástí kontraktu dat, musíte použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], můžete vždy použít zvláštní hodnota 0 (nula) na výčet, který je zároveň výchozí hodnotu pro libovolný výčet. Ale i tento speciální nulovou hodnotu nejde serializovat, pokud je označené atributem <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut.  
  
 Existují dvě výjimky:  
  
-   Příznak výčty (popsáno dále v tomto tématu).  
  
-   Datové členy výčtu s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> nastavenou na `false` (v takovém případě výčet s hodnotou nula je vynecháno z serializovaná data).  
  
### <a name="customizing-enumeration-member-values"></a>Úpravy hodnot členů výčtu  
 Hodnota člena výčtu, která tvoří součást kontraktu dat s využitím můžete přizpůsobit <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> vlastnost <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut.  
  
 Následující kontraktu dat je třeba také ekvivalentní s kontraktu dat `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Při serializován, hodnota `PreviouslyOwned` má reprezentaci XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Jednoduché výčty  
 Můžete také serializovat výčtové typy, ke kterému <xref:System.Runtime.Serialization.DataContractAttribute> nepoužil atribut. Takové výčet typy se považují přesně jak je uvedeno výše, s výjimkou, že každý člen (, která nemá <xref:System.NonSerializedAttribute> atribut) je zpracováván jako <xref:System.Runtime.Serialization.EnumMemberAttribute> byl použit atribut. Například následující výčet má implicitně kontraktu dat, která je ekvivalentní předchozí `CarConditionEnum` příklad.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Jednoduché výčty můžete použít při není potřeba přizpůsobit názvem kontraktu dat výčtu a obor názvů a hodnot člen výčtu.  
  
#### <a name="notes-on-simple-enumerations"></a>Poznámky k jednoduché výčty  
 Použití <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut na jednoduché výčty nemá žádný vliv.  
  
 Nezáleží na tom, zda je či není <xref:System.SerializableAttribute> atributu se použije pro výčet.  
  
 Fakt, který <xref:System.Runtime.Serialization.DataContractSerializer> třídy respektuje <xref:System.NonSerializedAttribute> použije pro členy výčtu se liší od chování <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Obě tyto serializátory Ignorovat <xref:System.NonSerializedAttribute> atribut.  
  
## <a name="flag-enumerations"></a>Příznak výčty  
 Můžete použít <xref:System.FlagsAttribute> atribut pro výčty. Seznam nula nebo více hodnot výčtu v takovém případě můžete odeslat ani přijmout současně.  
  
 Chcete-li tak učinit, použijte <xref:System.Runtime.Serialization.DataContractAttribute> atribut výčet příznaků a poté označte všechny členy, které jsou pro mocniny dvou s <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. Všimněte si, že pokud chcete použít výčet příznaků, musí být jeho průběh bez přerušení posloupnost mocninu 2 (například 1, 2, 4, 8, 16, 32, 64).  
  
 Následující postup se vztahuje k odesílání hodnota výčtu příznak, který:  
  
1.  Se pokusí vyhledat na člena výčtu (s <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut), která se mapuje na číselnou hodnotu. Pokud se nenašel, Odeslat seznam, který obsahuje pouze tohoto člena.  
  
2.  Pokoušejí o přerušení číselné hodnoty do součtu tak, že jsou členy výčtu (spolu <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut), která mapují na jednotlivých součástí tohoto součtu. Odešle seznam všech těchto členů. Všimněte si, že *greedy algoritmus* slouží k vyhledání součtu, a proto neexistuje žádná záruka, že takové součet se nachází i v případě, že je k dispozici. K tomuto problému vyhnout, ujistěte se, že se pro mocniny dvou číselných hodnot členy výčtu.  
  
3.  Pokud předchozí dva kroky nezdaří a je nenulovou číselnou hodnotu, výjimku <xref:System.Runtime.Serialization.SerializationException>. Pokud se číselná hodnota je nula, odeslat prázdný seznam.  
  
### <a name="example"></a>Příklad  
 Následující příklad výčtu lze použít v rámci operace příznak.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Následující ukázkové hodnoty serializují, jak je uvedeno.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
