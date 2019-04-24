---
title: Ekvivalence kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: a526a58ef801e91775756e6a84a94a066d32d284
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214933"
---
# <a name="data-contract-equivalence"></a>Ekvivalence kontraktů dat
Klient úspěšně odeslat data určitého typu na službu nebo služby k úspěšnému odeslání dat klientovi odeslané typ nutně nemusí existovat na přijímající straně. Jediným požadavkem je, že jako ekvivalentní, kontrakty dat obou typů. (V některých případech striktní ekvivalence se nevyžaduje, jak je popsáno v [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Pro datové kontrakty jako ekvivalentní musí mít stejný obor názvů a název. Kromě toho musí mít každý datový člen na jedné straně ekvivalentní datový člen na druhé straně.  
  
 Pro datové členy jako ekvivalentní musí mít stejný název. Kromě toho musí představovat stejný typ dat; To znamená musí být jejich kontraktů dat ekvivalentní.  
  
> [!NOTE]
>  Všimněte si, že data smlouvy názvy a obory názvů, jakož i názvy datových členů jsou malá a velká písmena.  
  
 Další informace o názvech kontraktů dat a obory názvů, jakož i názvy datových členů, naleznete v tématu [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Pokud existují dva typy na jedné straně (odesílatele a příjemce) a jejich data kontrakty nejsou ekvivalentní (například mají různé datové členy), by neměla je poskytnout stejný název a obor názvů. To může způsobit, že výjimky, která je vyvolána.  
  
 Kontrakty dat pro následující typy jsou ekvivalentní:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Ekvivalence pořadí datových členů a kontrakt dat  
 Použití <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> třída může mít vliv na ekvivalence kontraktů dat. Kontrakty dat musí obsahovat členy, které se zobrazují ve stejném pořadí jako ekvivalentní. Výchozí pořadí je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Například následující kód za následek ekvivalentní datové kontrakty.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Ale následující nemá za následek kontrakt ekvivalentní data.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dědičnost, rozhraní a ekvivalence kontraktů dat  
 Při určování ekvivalence kontraktu dat, která dědí z jiné kontraktu dat. je zpracováván, pokud je pouze jeden kontrakt dat, který obsahuje všechny datové členy ze základního typu. Mějte na paměti, že musí odpovídat pořadí datových členů a že předcházet členy základního typu odvozené členů typů v pořadí. Kromě toho pokud dva datové členy jako v následujícím příkladu kódu mají stejnou hodnotu pořadí, řazení pro tyto datové členy je abecední. Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu kontraktu dat pro typ `Employee` odpovídá kontraktu dat pro typ `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Při předávání parametrů a vrácených hodnot mezi klientem a službou, kontrakt dat ze základní třídy nelze odeslat při přijímání koncový bod očekává, že kontrakt dat z odvozené třídy. Toto je v souladu s objektově orientované programování zásady. V předchozím příkladu, objekt typu `Person` nelze odeslat, když `Employee` očekává.  
  
 Kontrakt dat z odvozené třídy mohou zasílat kontraktu dat ze základní třídy je očekávané, ale pouze v případě přijímající koncového bodu "ví" použití odvozený typ <xref:System.Runtime.Serialization.KnownTypeAttribute>. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). V předchozím příkladu, objekt typu `Employee` mohou být odesílány při `Person` je očekávané, ale pouze v případě, že příjemce kód využívá <xref:System.Runtime.Serialization.KnownTypeAttribute> se zahrnuje do seznamu známých typů.  
  
 Při předávání parametrů a vrácených hodnot mezi aplikacemi, pokud očekávaný typ je rozhraní, je ekvivalentní k očekávaný typ je typ <xref:System.Object>. Vzhledem k tomu, že každý typ, takže v konečném důsledku je odvozena z <xref:System.Object>, každý kontraktu dat takže v konečném důsledku je odvozena z kontraktu dat pro <xref:System.Object>. Proto je možné předat libovolný typ kontraktu dat při očekávání rozhraní. Je potřeba provést další kroky úspěšně práci s rozhraními; Další informace najdete v tématu [známé typy kontraktů dat.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
