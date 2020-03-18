---
title: Přehled názvových prostorů (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d5f176a5561b77126ef23af996ab1e4bf51092ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868828"
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled názvových prostorů (LINQ to XML)

Tento článek představuje obory <xref:System.Xml.Linq.XName> názvů, <xref:System.Xml.Linq.XNamespace> třídy a třídy.

## <a name="xml-names"></a>Názvy XML

Názvy XML jsou často zdrojem složitosti programování XML. Název XML se skládá z oboru názvů XML (nazývaného také identifikátor URI oboru názvů XML) a místního názvu. Obor názvů XML je podobný oboru názvů v programu založeném na rozhraní .NET Framework. Umožňuje jedinečně kvalifikovat názvy prvků a atributů. To pomáhá zabránit konfliktům názvů mezi různými částmi dokumentu XML. Pokud jste deklarovali obor názvů XML, můžete vybrat místní název, který musí být jedinečný pouze v tomto oboru názvů.

Dalším aspektem názvů XML jsou *předpony oboru názvů*XML . Předpony XML způsobují většinu složitosti názvů XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, díky čemuž je dokument XML stručnější a srozumitelnější. Předpony XML však závisí na jejich kontextu, aby měly význam, což zvyšuje složitost. Předpona XML může `aw` být například přidružena k jednomu oboru názvů XML v jedné části stromu XML a k jinému oboru názvů XML v jiné části stromu XML.

Jednou z výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] použití s C# je, že není třeba používat předpony XML. Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načtete nebo analyzujete dokument XML, každá předpona XML je přeložena do odpovídajícího oboru názvů XML. Poté při práci s dokumentem, který používá obory názvů, téměř vždy přistupujete k oborům názvů prostřednictvím identifikátoru URI oboru názvů, nikoli prostřednictvím předpony oboru názvů. Když vývojáři pracují [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s názvy XML v jevždy pracovat s plně kvalifikovaný název XML (to znamená, že obor názvů XML a místní název). V případě potřeby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] však umožňuje pracovat s předpony oboru názvů a řídit je.

V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace je <xref:System.Xml.Linq.XName>třída, která představuje názvy XML . Názvy XML se [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] často objevují v celém rozhraní API a <xref:System.Xml.Linq.XName> všude tam, kde je vyžadován název XML, najdete parametr. Zřídka však pracujete přímo <xref:System.Xml.Linq.XName>s . <xref:System.Xml.Linq.XName>obsahuje implicitní převod z řetězce.

Další informace naleznete v tématech <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.
