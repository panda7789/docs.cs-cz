---
title: "Názvy kontraktu dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da7cb5e30cd4c8c5bf59c45b5e38d766990275b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-names"></a>Názvy kontraktu dat
Stejné typy někdy nesdílejí klienta a služby. Stále se můžete předat data do sebe navzájem tak dlouho, dokud kontrakty dat odpovídají na obou stranách. [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md) je založena na kontrakt dat a názvy datových členů, a proto se poskytuje mechanismus pro mapování typů a členů do těchto názvů. Toto téma popisuje pravidla pro pojmenovávání kontrakty dat a také výchozí chování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury při vytváření názvů.  
  
## <a name="basic-rules"></a>Základních pravidel  
 Základní pravidla týkající se pojmenování data, která smlouvy zahrnují:  
  
-   Data plně kvalifikovaný název kontraktu se skládá z oboru názvů a název.  
  
-   Datové členy mít pouze názvy, ale žádné obory názvů.  
  
-   Při zpracování datové kontrakty, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury je malá a velká písmena obory názvů a názvy kontrakty dat a datových členů.  
  
## <a name="data-contract-namespaces"></a>Obory názvů kontraktu dat  
 Obor názvů kontraktu dat má formu z identifikátor URI (Uniform Resource). Identifikátor URI může být absolutní nebo relativní. Ve výchozím nastavení přiřazené kontrakty dat pro určitý typ oboru názvů, který pochází z běžných language runtime (CLR) obor názvů typu.  
  
 Ve výchozím nastavení jsou všechny daném oboru názvů CLR (ve formátu *Clr.Namespace*) je namapovaný na obor názvů "http://schemas.datacontract.org/2004/07/Clr.Namespace". Pokud chcete přepsat toto výchozí nastavení, použít <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atribut celého modulu nebo sestavení. Můžete taky řídit obor názvů kontraktu dat pro každý typ, nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
> [!NOTE]
>  Obor názvů "http://schemas.microsoft.com/2003/10/Serialization" je vyhrazena a nelze použít jako obor názvů kontraktu dat.  
  
> [!NOTE]
>  Nejde přepsat výchozí obor názvů v typy kontraktů dat, které obsahují `delegate` deklarace.  
  
## <a name="data-contract-names"></a>Názvy kontraktu dat  
 Výchozí název kontraktu dat pro daný typ je název tohoto typu. Chcete-li přepsat výchozí nastavení, nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute> alternativní název. Zvláštní pravidla pro obecné typy jsou popsané v "Data kontrakt názvy pro obecné typy" dál v tomto tématu.  
  
## <a name="data-member-names"></a>Názvy datových členů  
 Výchozí název člena dat pro dané pole nebo vlastnosti je název tohoto pole nebo vlastnost. Chcete-li přepsat výchozí nastavení, nastavte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> na alternativní hodnotu.  
  
### <a name="examples"></a>Příklady  
 Následující příklad ukazuje, jak můžete přepsat výchozí názvový chování kontrakty dat a datových členů.  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>Názvy kontraktu dat pro obecné typy  
 Existují zvláštní pravidla pro určování názvy kontraktu dat pro obecné typy. Tato pravidla vyhnout kolize názvů kontraktu dat mezi dvěma uzavřené obecné stejného obecného typu.  
  
 Ve výchozím nastavení, název kontraktu dat pro obecný typ je název typu, za nímž následuje řetězec "", za nímž následuje názvy kontraktu dat obecné parametry, za nímž následuje *hash* vypočítány pomocí názvů kontraktu dat Obecné parametry. Hodnota hash je výsledkem matematické funkce, který funguje jako "otisk prstu" jedinečně identifikující část data. Když jsou všechny obecné parametry primitivní typy, hodnota hash je vynechán.  
  
 Například zobrazit typy v následujícím příkladu.  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 V tomto příkladu typ `Drawing<Square,RegularRedBrush>` má název kontraktu dat "DrawingOfSquareRedBrush5HWGAU6h", kde "5HWGAU6h" je hodnota hash "urn: tvary" a "urn: výchozí" obory názvů. Typ `Drawing<Square,SpecialRedBrush>` má název kontraktu dat "DrawingOfSquareRedBrushjpB5LgQ_S", kde "jpB5LgQ_S" je hodnota hash "urn: tvary" a "urn: zvláštní" obory názvů. Upozorňujeme, že pokud se nepoužívá algoritmus hash, dva názvy jsou identické a tím dojde k kolize názvů.  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>Přizpůsobení názvy datových kontraktů obecné typy  
 V některých případech jsou názvy datových kontraktů vygenerované obecných typů, jak je popsáno výše, nepřijatelné. Například můžete vědět předem do kolize názvů se nespustí a může být nutné odebrat hodnotu hash. V takovém případě můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost `DataContractAttribute` atribut zadat jiný způsob, jak vygenerovat názvy. Můžete použít čísla do složených závorek uvnitř `Name` vlastnost, která má odkazovat na data názvy kontraktu obecné parametry. (odkazuje na první parametr 0, 1 odkazuje na druhé atd.) Znak čísla (#) uvnitř složené závorky slouží k odkazování na hodnotu hash. Můžete použít všechny tyto odkazy vícekrát nebo vůbec.  
  
 Například předchozím Obecné `Drawing` typu by byli deklarováni jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 V tomto případě typ `Drawing<Square,RegularRedBrush>` má název kontraktu dat "Drawing_using_RedBrush_brush_and_Square_shape". Všimněte si, že vzhledem k tomu, že je "{#}" v <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost, hash není součástí názvu, a proto je ohrožena útoky založenými na pojmenování typ kolize, například typ `Drawing<Square,SpecialRedBrush>` by mít přesně stejný název kontraktu dat.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Názvy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
