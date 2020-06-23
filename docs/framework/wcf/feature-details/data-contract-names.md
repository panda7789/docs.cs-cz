---
title: Názvy kontraktu dat
description: Zjistěte kontrakt dat a pravidla pro pojmenovávání členů a výchozí chování infrastruktury WCF, které podporují komunikaci pomocí ekvivalentních kontraktů dat.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 85c533d683558520d46f259db0bdb34dcb1214c9
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247400"
---
# <a name="data-contract-names"></a>Názvy kontraktu dat

V některých případech klient a služba nesdílejí stejné typy. Mohou i nadále předávat data, dokud jsou kontrakty dat rovnocenné na obou stranách. [Ekvivalence kontraktů dat](data-contract-equivalence.md) je založena na názvech kontraktů dat a datových členů, a proto je k dispozici mechanismus pro mapování typů a členů na tyto názvy. Toto téma vysvětluje pravidla pro pojmenovávání kontraktů dat a také výchozí chování infrastruktury Windows Communication Foundation (WCF) při vytváření názvů.

## <a name="basic-rules"></a>Základní pravidla
Mezi základní pravidla týkající se názvů kontraktů dat patří:

- Plně kvalifikovaný název kontraktu dat se skládá z oboru názvů a názvu.

- Datové členy mají pouze názvy, ale žádné obory názvů.

- Při zpracování kontraktů dat se v infrastruktuře WCF rozlišují velká a malá písmena pro obory názvů a názvy kontraktů dat a datových členů.

## <a name="data-contract-namespaces"></a>Obory názvů kontraktu dat
Obor názvů kontraktu dat má formu identifikátoru URI (Uniform Resource Identifier). Identifikátor URI může být buď absolutní, nebo relativní. Ve výchozím nastavení jsou kontrakty dat pro určitý typ přiřazeny k oboru názvů, který pochází z oboru názvů Common Language Runtime (CLR) daného typu.

Ve výchozím nastavení jsou všechny zadané obory názvů CLR (ve formátu *CLR. Namespace*) namapovány na obor názvů `http://schemas.datacontract.org/2004/07/Clr.Namespace` . Chcete-li přepsat toto výchozí nastavení, použijte <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atribut pro celý modul nebo sestavení. Případně pro řízení oboru názvů kontraktu dat pro každý typ nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> vlastnost <xref:System.Runtime.Serialization.DataContractAttribute> .

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization`Obor názvů je rezervovaný a nedá se použít jako obor názvů kontraktu dat.

> [!NOTE]
> Výchozí obor názvů nelze přepsat v typech kontraktů dat, které obsahují `delegate` deklarace.

## <a name="data-contract-names"></a>Názvy kontraktu dat
Výchozí název kontraktu dat pro daný typ je název tohoto typu. Chcete-li přepsat výchozí hodnotu, nastavte <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> vlastnost na <xref:System.Runtime.Serialization.DataContractAttribute> alternativní název. Zvláštní pravidla pro obecné typy jsou popsána v části "názvy kontraktů dat pro obecné typy" dále v tomto tématu.

## <a name="data-member-names"></a>Názvy datových členů
Výchozím názvem datového členu pro dané pole nebo vlastnost je název daného pole nebo vlastnosti. Pro přepsání výchozí <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> hodnoty nastavte vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> na jinou hodnotu.

### <a name="examples"></a>Příklady
Následující příklad ukazuje, jak můžete přepsat výchozí chování při pojmenovávání kontraktů dat a datových členů.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Názvy kontraktů dat pro obecné typy
Pro určení názvů kontraktů dat pro obecné typy existují zvláštní pravidla. Tato pravidla zabraňují kolizi názvů kontraktů dat mezi dvěma uzavřenými obecnými typy stejného obecného typu.

Ve výchozím nastavení je název kontraktu dat pro obecný typ název typu následovaný řetězcem "of" následovaným názvy kontraktů dat obecných parametrů následovaným *hodnotou hash* vypočítanou pomocí oborů názvů kontraktu dat obecných parametrů. Hodnota hash je výsledkem matematické funkce, která funguje jako "otisk", který jednoznačně identifikuje část dat. Pokud jsou všechny obecné parametry primitivní typy, je hodnota hash vynechána.

Podívejte se například na typy v následujícím příkladu.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

V tomto příkladu `Drawing<Square,RegularRedBrush>` má typ název kontraktu dat "DrawingOfSquareRedBrush5HWGAU6h", kde "5HWGAU6h" je hodnota hash "urn: Shapes" a "urn: default" Namespaces. Typ `Drawing<Square,SpecialRedBrush>` má název kontraktu dat "DrawingOfSquareRedBrushjpB5LgQ_S", kde "jpB5LgQ_S" je hodnota hash "urn: Shapes" a "urn: Special" Namespaces. Všimněte si, že pokud se hodnota hash nepoužívá, jsou tyto dva názvy identické, a proto dojde ke kolizi názvů.

## <a name="customizing-data-contract-names-for-generic-types"></a>Přizpůsobení názvů kontraktů dat pro obecné typy

Někdy nejsou přijatelné názvy kontraktů dat vygenerované pro obecné typy, jak je popsáno výše. Můžete například určit, že se nebudete muset zacházet do kolizí názvů a může chtít odebrat hodnotu hash. V takovém případě můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> vlastnost k určení jiného způsobu generování názvů. Čísla ve složených závorkách uvnitř vlastnosti můžete použít `Name` k odkazování na názvy kontraktů dat obecných parametrů. (0 odkazuje na první parametr, 1 odkazuje na druhý atd.) Pokud chcete odkazovat na hodnotu hash, můžete v složených závorkách použít znak (#). Každý z těchto odkazů můžete použít vícekrát nebo vůbec.

Například předchozí obecný `Drawing` typ mohl být deklarován, jak je znázorněno v následujícím příkladu.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

V tomto případě `Drawing<Square,RegularRedBrush>` má typ název kontraktu dat "Drawing_using_RedBrush_brush_and_Square_shape". Všimněte si, že vzhledem k tomu, že ve vlastnosti existuje "{#}" <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> , hodnota hash není součástí názvu, a proto je typ náchyln k kolizí názvů; například typ `Drawing<Square,SpecialRedBrush>` by měl přesně stejný název kontraktu dat.

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Použití kontraktů dat](using-data-contracts.md)
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Názvy kontraktu dat](data-contract-names.md)
- [Správa verzí kontraktů dat](data-contract-versioning.md)
