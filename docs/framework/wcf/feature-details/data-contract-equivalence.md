---
title: Ekvivalence kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: b6461ffe6525b377e7f836a686a401033d344a4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492792"
---
# <a name="data-contract-equivalence"></a>Ekvivalence kontraktů dat
Pro klienta k úspěšnému odeslání dat určitého typu služby nebo k službě úspěšně posílat data do klienta odeslané typ nemusí nutně existovat na koncové straně příjmu. Jediným požadavkem je, že kontrakty dat obou typů být ekvivalentní. (V některých případech striktní ekvivalenční se nevyžaduje, jak je popsáno v [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Pro datové kontrakty jako ekvivalentní musí mít stejný obor názvů a název. Kromě toho musí mít každý člen data na jedné straně člena ekvivalentní datové na druhé straně.  
  
 Pro datové členy jako ekvivalentní musí mít stejný název. Kromě toho musí představovat stejný typ dat; To znamená musí být jejich kontrakty dat ekvivalentní.  
  
> [!NOTE]
>  Všimněte si, že kontraktů dat názvy a obory názvů, jakož i názvy datových členů malých a velkých písmen.  
  
 Další informace o názvy kontraktu dat a obory názvů a názvy členů dat najdete v tématu [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Pokud existují dva typy na jedné straně (odesílatel nebo příjemce) a jejich kontrakty dat nejsou ekvivalentní (například mají různé datové členy), by neměl jim poskytnout se stejným názvem a oborem názvů. Díky tomu může způsobit vyvolání výjimky.  
  
 Kontrakty dat pro následující typy jsou ekvivalentní:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Ekvivalence pořadí datových členů a kontrakt dat  
 Pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> třída může mít vliv na ekvivalence kontraktů dat. Kontrakty dat musí mít členy, které se zobrazují ve stejném pořadí jako ekvivalentní. Výchozí pořadí je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Například následující kód výsledkem ekvivalentní datové kontrakty.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ale následující nevede ekvivalentní datové kontrakt.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dědičnost, rozhraní a ekvivalence kontraktů dat  
 Při určování ekvivalenční, považuje kontraktu dat, která dědí z jiné kontrakt dat, pokud je pouze jeden kontrakt dat, která zahrnuje všechny členy data ze základního typu. Mějte na paměti, která se musí shodovat s pořadí datových členů a že předcházet členy základní typ odvozený typ členy v pořadí. Navíc pokud dva data členů jako v následujícím příkladu kódu mají stejnou hodnotu pořadí, řazení pro členy těchto dat je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu kontraktu dat pro typ `Employee` je ekvivalentní kontrakt dat pro typ `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Při předávání parametry a návratové hodnoty mezi klientem a služby, kontrakt dat z databáze třídu, nelze odeslat při příjmu koncový bod očekává kontraktu dat z odvozené třídy. Toto je v souladu s objektově orientované programování principů. V předchozím příkladu, objekt typu `Person` nelze odeslat, kdy `Employee` se očekává.  
  
 Kontrakt dat z odvozené třídy lze odeslat při kontraktu dat z databáze třídu, očekává se, ale pouze v případě, že přijímající koncový bod "ví" odvozený typ použití <xref:System.Runtime.Serialization.KnownTypeAttribute>. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). V předchozím příkladu, objekt typu `Employee` lze odeslat při `Person` je očekávané, ale pouze v případě, že kód příjemce aktivuje <xref:System.Runtime.Serialization.KnownTypeAttribute> chcete zahrnout do seznamu známých typů.  
  
 Při předávání parametry a návratové hodnoty mezi aplikacemi, pokud očekávaný typ je rozhraní, je ekvivalentní očekávaný typ je typ <xref:System.Object>. Protože každý typ výsledku odvozen z <xref:System.Object>, každý kontrakt dat nakonec odvozuje od kontrakt dat pro <xref:System.Object>. Proto může být libovolný typ kontraktu dat předán očekávaném rozhraní. Další kroky jsou nutné k úspěšně práci s rozhraními; Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
