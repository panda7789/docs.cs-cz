---
title: Výčtové typy v kontraktech dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: ed4a0c572f651793a40cb5ffcaa32aef884c1cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494514"
---
# <a name="enumeration-types-in-data-contracts"></a>Výčtové typy v kontraktech dat
Výčty může být vyjádřený v datovém modelu kontrakt. Toto téma vás provede několik příkladů, které vysvětlují programovací model.  
  
## <a name="enumeration-basics"></a>Základy – výčet  
 Jeden ze způsobů použití výčtové typy v modelu kontraktu dat je pro použití <xref:System.Runtime.Serialization.DataContractAttribute> atributu typu. Musíte použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut pro každého člena, který musí být součástí kontrakt dat.  
  
 Následující příklad ukazuje dvě třídy. Používá výčtu první a druhý definuje výčtu.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Instance `Car` třída může odesílat nebo přijímat pouze v případě `condition` je nastaveno na jednu z hodnot `New`, `Used`, nebo `Rental`. Pokud `condition` je `Broken` nebo `Stolen`, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.  
  
 Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> vlastnosti (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> a <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) jako obvykle pro kontrakty dat výčtu.  
  
### <a name="enumeration-member-values"></a>Hodnoty člen výčtu  
 Obecně kontrakt dat zahrnuje názvy členů výčtu, nikoli číselné hodnoty. Při použití datového modelu kontrakt, pokud je klient WCF straně příjmu, ale schéma exportovaný zachová číselné hodnoty. Všimněte si, že to tak není při použití [používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 V předchozím příkladu Pokud `condition` je nastaven na `Used` a je serializovat data XML, je výsledný soubor XML `<condition>Used</condition>` a není `<condition>1</condition>`. Proto je ekvivalentní kontrakt dat z následující kontrakt dat `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Například můžete použít `CarConditionEnum` na straně odesílání a `CarConditionWithNumbers` na straně příjmu. I když na odesílající straně používá hodnotu "1" pro `Used` a přijímající straně používá, je hodnota "20," reprezentaci XML `<condition>Used</condition>` pro obou stranách.  
  
 Chcete-li být součástí kontrakt dat, je nutné použít <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], můžete vždy použít speciální hodnota 0 (nula) pro výčet, který je taky výchozí hodnota pro všechny – výčet. Ale i v této zvláštní nulovou hodnotu nelze serializovat, pokud je označené <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut.  
  
 Existují dvě výjimky:  
  
-   Příznak výčty (popsané dál v tomto tématu).  
  
-   Datové členy výčtu s <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> vlastnost nastavena na hodnotu `false` (v takovém případě výčtu s nulovou hodnotou je vynechaný serializovaná data).  
  
### <a name="customizing-enumeration-member-values"></a>Přizpůsobení hodnot člen výčtu  
 Můžete upravit hodnotu člena výčtu, která součástí kontrakt dat pomocí <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> vlastnost <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut.  
  
 Například následující kontrakt dat odpovídá také kontrakt dat z `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Když serializovanou hodnotu `PreviouslyOwned` má reprezentaci XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Jednoduché výčty  
 Můžete také serializovat výčtové typy, ke kterému <xref:System.Runtime.Serialization.DataContractAttribute> atribut nebyla použita. Takové výčtové typy jsou považovány přesně podle předchozích pokynů, vyjma toho, že každý člen (která nemá <xref:System.NonSerializedAttribute> atribut použitý) považuje jako kdyby <xref:System.Runtime.Serialization.EnumMemberAttribute> byl použit atribut. Například následující výčet implicitně má ekvivalentní předchozím kontraktu dat `CarConditionEnum` příklad.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Jednoduché výčty můžete použít, když není potřeba přizpůsobit název kontraktu dat ve výčtu a obor názvů a hodnot člen výčtu.  
  
#### <a name="notes-on-simple-enumerations"></a>Poznámky k jednoduché výčty  
 Použití <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut na jednoduchý výčty nemá žádný vliv.  
  
 Nezáleží na tom, jestli <xref:System.SerializableAttribute> výčtu je použit atribut.  
  
 Fakt, <xref:System.Runtime.Serialization.DataContractSerializer> třídy respektuje <xref:System.NonSerializedAttribute> atributu použitého pro členy výčtu se liší od chování <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Obě tyto serializátorů Ignorovat <xref:System.NonSerializedAttribute> atribut.  
  
## <a name="flag-enumerations"></a>Příznak výčty  
 Můžete použít <xref:System.FlagsAttribute> atribut výčty. V takovém případě seznam nula nebo více hodnot výčtu můžete odeslat nebo současně.  
  
 K tomu použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut výčet příznaků a označí všechny členy, kteří jsou dva pravomocí <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. Všimněte si, že pokud chcete použít výčet příznaků, musí být průběh v bez přerušení sekvenci zajišťuje 2 (například 1, 2, 4, 8, 16, 32, 64).  
  
 Následující postup se vztahuje k odesílání Příznak Hodnota výčtu:  
  
1.  Pokus o vyhledání člena výčtu (s <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut použitý) která se mapuje na číselnou hodnotu. Pokud nalezen, odeslání seznamu, který právě tohoto člena obsahuje.  
  
2.  Pokus o rozdělit číselnou hodnotu na součet tak, že jsou členy výčtu (každý <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut použitý), mapování na jednotlivých součástí součet. Odesílání seznamu všech těchto členů. Všimněte si, že *typu greedy algoritmus* se používá k vyhledání sum, a proto není zaručeno, například součet nalezené i v případě, že je k dispozici. K tomuto problému nedošlo, ujistěte se, že číselné hodnoty výčtu členy, jsou zajišťuje dva.  
  
3.  Pokud předchozí dva kroky k selhání, a je číselná hodnota nenulové hodnoty, throw <xref:System.Runtime.Serialization.SerializationException>. Pokud je číselná hodnota nulová, odeslat prázdný seznam.  
  
### <a name="example"></a>Příklad  
 Následující příklad výčet můžete použít v operaci příznak.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Následující ukázkové hodnoty jsou serializovat jako uvedené.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
