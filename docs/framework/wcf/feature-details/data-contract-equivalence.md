---
title: Ekvivalence kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: 448c47d8687aa32671ade016f9b48cd763f87dfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945364"
---
# <a name="data-contract-equivalence"></a>Ekvivalence kontraktů dat
Aby mohl klient úspěšně odeslat data určitého typu do služby nebo služba, aby úspěšně odesílala data klientovi, odeslaný typ nemusí nutně existovat na přijímací straně. Jediným požadavkem je, že kontrakty dat obou typů jsou ekvivalentní. (V některých případech se striktní rovnost nevyžaduje, jak je popsáno v tématu [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Aby byly kontrakty dat rovnocenné, musí mít stejný obor názvů a název. Kromě toho musí mít každý datový člen na jedné straně ekvivalentní datový člen na druhé straně.  
  
 Aby datové členy byly ekvivalentní, musí mít stejný název. Navíc musí představovat stejný typ dat; To znamená, že jejich kontrakty dat musí být ekvivalentní.  
  
> [!NOTE]
> Všimněte si, že názvy kontraktů dat a obory názvů a také názvy datových členů rozlišují velká a malá písmena.  
  
 Další informace o názvech kontraktů dat a oborech názvů a také o názvech datových členů najdete v tématu [názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Pokud existují dva typy na stejné straně (odesílatel nebo přijímač) a jejich kontrakty dat nejsou ekvivalentní (například mají různé datové členy), neměli byste jim mít stejný název a obor názvů. V takovém případě může dojít k vyvolání výjimek.  
  
 Kontrakty dat pro následující typy jsou ekvivalentní:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Pořadí datových členů a rovnocennosti kontraktu dat  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Použití vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> třídy může ovlivnit ekvivalenci kontraktu dat. Kontrakty dat musí mít členy, které se zobrazí ve stejném pořadí jako ekvivalentní. Výchozí pořadí je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Například následující kód má za následek ekvivalentní kontrakty dat.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Následující akce ale nevede ke stejnému kontraktu dat.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dědičnost, rozhraní a ekvivalent kontraktu dat  
 Při určování rovnocennosti je kontrakt dat, který dědí z jiné kontraktu dat, považován za, jako by se jednalo o pouze jeden kontrakt dat, který obsahuje všechny datové členy ze základního typu. Mějte na paměti, že pořadí datových členů musí odpovídat a že členové základního typu předcházejí odvozené typy členů v pořadí. Kromě toho, pokud, jak je uvedeno v následujícím příkladu kódu, dva datové členy mají stejnou hodnotu Order, pořadí těchto datových členů je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu je kontrakt dat pro typ `Employee` ekvivalentní kontraktu dat pro daný typ. `Worker`  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Při předávání parametrů a vrácení hodnot mezi klientem a službou nelze odeslat kontrakt dat ze základní třídy, pokud přijímající koncový bod očekává kontrakt dat z odvozené třídy. To je v souladu s objektově orientovaným programovacím principy. V předchozím příkladu nelze objekt typu `Person` odeslat, `Employee` když je očekáváno klíčové slovo.  
  
 Kontrakt dat z odvozené třídy lze odeslat při očekávání kontraktu dat ze základní třídy, ale pouze v případě, že přijímající koncový bod "zná" odvozeného typu pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). V předchozím příkladu `Employee` `Person` je možné odeslat objekt typu, když je očekáváno, ale pouze v případě, že kód <xref:System.Runtime.Serialization.KnownTypeAttribute> příjemce používá pro zahrnutí do seznamu známých typů.  
  
 Při předávání parametrů a vrácení hodnot mezi aplikacemi, pokud je očekávaný typ rozhraní, je ekvivalentní očekávanému typu <xref:System.Object>typu. Vzhledem k tomu, že každý typ <xref:System.Object>je nakonec odvozen z, každý kontrakt dat je nakonec odvozen od <xref:System.Object>kontraktu dat pro. Proto je možné předat libovolný typ kontraktu dat, když je očekáváno rozhraní. Pro úspěšnou práci s rozhraními jsou nutné další kroky. Další informace najdete v tématu [známé typy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
