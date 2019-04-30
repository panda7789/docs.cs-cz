---
title: Názvy kontraktu dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 16a42a2808104a77e56e93564a679dfc578e73f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857272"
---
# <a name="data-contract-names"></a>Názvy kontraktu dat

Stejné typy někdy nesdílejí klienta a služby. Stále, můžete předat data do sebe navzájem kontraktů dat jsou ekvivalentní na obou stranách. [Ekvivalence kontraktů dat](data-contract-equivalence.md) vychází kontraktu dat a názvy datových členů, a proto poskytuje mechanismus pro mapování typů a členů na tyto názvy. Toto téma popisuje pravidla pro vytváření názvů kontraktů dat, stejně jako výchozí chování infrastruktury Windows Communication Foundation (WCF) při vytváření názvů.

## <a name="basic-rules"></a>Základní pravidla
Základní pravidla týkající se názvů data, která zahrnují smlouvy:

- Název kontraktu dat plně kvalifikovaný se skládá z oboru názvů a název.

- Datové členy mají pouze názvy, ale žádné obory názvů.

- Při zpracování kontraktů dat, infrastruktura WCF je malá a velká písmena na obory názvů a názvy kontraktů dat a datové členy.

## <a name="data-contract-namespaces"></a>Obory názvů kontraktu dat
Obor názvů kontraktu dat má podobu z identifikátor URI (Uniform Resource). Identifikátor URI může být absolutní nebo relativní. Ve výchozím nastavení jsou přiřazeny kontraktů dat pro určitý typ oboru názvů, který přichází z běžné language runtime (CLR) oboru názvů typu.

Ve výchozím nastavení, libovolný daný obor názvů CLR (ve formátu *Clr.Namespace*) je namapovaný na obor názvů `http://schemas.datacontract.org/2004/07/Clr.Namespace`. Chcete-li přepsat toto výchozí nastavení, použijte <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atributu na celý modul nebo sestavení. Můžete také určit obor názvů kontraktu dat pro každý typ, nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute>.

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization` Obor názvů je vyhrazené a nejde použít jako obor názvů kontraktu dat.

> [!NOTE]
> Nejde přepsat výchozí obor názvů v typy kontraktu dat, které obsahují `delegate` deklarace.

## <a name="data-contract-names"></a>Názvy kontraktu dat
Výchozí název kontraktu dat pro daný typ je název tohoto typu. Chcete-li přepsat výchozí hodnotu, nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute> alternativní název. Zvláštní pravidla pro obecné typy jsou popsány v "Data názvy pro obecné typy kontraktů" dále v tomto tématu.

## <a name="data-member-names"></a>Názvy datových členů
Výchozí název datový člen daného pole nebo vlastnosti je název pole nebo vlastnost. Chcete-li přepsat výchozí hodnotu, nastavte <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> alternativní hodnotě.

### <a name="examples"></a>Příklady
Následující příklad ukazuje, jak můžete přepsat výchozí názvový chování kontraktech dat a datové členy.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Názvy kontraktů dat pro obecné typy
Existují zvláštní pravidla pro určování názvů kontraktu dat pro obecné typy. Tato pravidla pomáhají vyhnete kolize názvů kontraktu dat mezi dvěma uzavřených obecných typů stejného obecného typu.

Ve výchozím nastavení, název kontraktu dat pro obecný typ není název typu, za nímž následuje řetězec "", za nímž následuje názvů kontraktu dat obecné parametry, za nímž následuje *hash* vypočítán s použitím názvů kontraktu dat Obecné parametry. Hodnota hash je výsledkem matematické funkce, která funguje jako "otisk prstu", který jednoznačně identifikuje část data. Když jsou všechny obecné parametry primitivní typy, je vynechána, hodnoty hash.

Například zobrazení typů v následujícím příkladu.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

V tomto příkladu typ `Drawing<Square,RegularRedBrush>` má název kontraktu dat "DrawingOfSquareRedBrush5HWGAU6h", kde "5HWGAU6h" je hodnota hash "urn: tvary" a "urn: výchozí" obory názvů. Typ `Drawing<Square,SpecialRedBrush>` má název kontraktu dat "DrawingOfSquareRedBrushjpB5LgQ_S", kde "jpB5LgQ_S" je hodnota hash "urn: tvary" a "urn: zvláštní" obory názvů. Všimněte si, že pokud se nepoužívá-the-hash, dva názvy jsou identické a tím dojde k kolize názvů.

## <a name="customizing-data-contract-names-for-generic-types"></a>Přizpůsobení názvů kontraktu dat pro obecné typy

V některých případech jsou názvy datových kontraktů vygenerované pro obecné typy, jak je popsáno výše, nepřijatelné. Například můžete vědět předem do kolize názvů se nespustí a může být vhodné odebrat-the-hash. V takovém případě můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> vlastnosti k určení způsobu, jak generovat názvy. Můžete použít číslice ve složených závorkách uvnitř `Name` vlastnost odkazovat na data názvy kontraktů obecné parametry. (0 označuje první parametr, 1 odkazuje na druhé atd.) Znak čísla (#) uvnitř složených závorek můžete použít k odkazování na-the-hash. Můžete použít každý z těchto odkazů vícekrát nebo vůbec.

Například předchozí obecný `Drawing` typ může být deklarovány jak je znázorněno v následujícím příkladu.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

V tomto případě, typ `Drawing<Square,RegularRedBrush>` má název kontraktu dat "Drawing_using_RedBrush_brush_and_Square_shape". Upozorňujeme, že je "{#}" v <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost,-the-hash není součástí názvu a proto je náchylný k pojmenování typ kolize, například typ `Drawing<Square,SpecialRedBrush>` bude mít přesně stejný název kontraktu dat.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Použití kontraktů dat](using-data-contracts.md)
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Názvy kontraktů dat](data-contract-names.md)
- [Správa verzí kontraktů dat](data-contract-versioning.md)
