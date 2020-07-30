---
title: Přehled názvových prostorů (LINQ to XML)
description: Zaveďte sami sebe do oborů názvů, třídy XName, třídy XNamespace a dalších aspektů názvů XML.
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 56dca481dd5f3066fa5359fc57b3311cf2569ee0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300160"
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled názvových prostorů (LINQ to XML)

Tento článek představuje obory názvů, <xref:System.Xml.Linq.XName> třídu a <xref:System.Xml.Linq.XNamespace> třídu.

## <a name="xml-names"></a>Názvy XML

Názvy XML jsou často zdrojem složitosti při programování XML. Název XML se skládá z oboru názvů XML (označuje se také jako identifikátor URI oboru názvů XML) a místního názvu. Obor názvů XML je podobný oboru názvů v programu .NET. Umožňuje jednoznačně kvalifikovat názvy elementů a atributů. To pomáhá zabránit konfliktu názvů mezi různými částmi dokumentu XML. Pokud jste deklarovali obor názvů XML, můžete vybrat místní název, který musí být v rámci tohoto oboru názvů jedinečný.

Dalším aspektem názvů XML jsou *předpony oboru názvů*XML. Předpony XML způsobují většinu složitosti názvů XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, díky čemuž je dokument XML výstižnější a srozumitelný. Předpony XML jsou však závislé na jejich kontextu a mají význam, což zvyšuje složitost. Předpona XML `aw` může být například přidružena k jednomu oboru názvů XML v jedné části stromu XML a s jiným oborem názvů XML v jiné části stromu XML.

Jednou z výhod použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce C# je, že nemusíte používat předpony XML. Při [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načítání nebo analýze dokumentu XML je každá předpona XML přeložena na odpovídající obor názvů XML. Po tom, když pracujete s dokumentem, který používá obory názvů, skoro vždy získáte přístup k oborům názvů prostřednictvím identifikátoru URI oboru názvů a nikoli prostřednictvím předpony oboru názvů. Když vývojáři pracují s názvy XML v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , vždy pracují s plně kvalifikovaným názvem XML (tj. obor názvů XML a místní název). V případě potřeby ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje pracovat s a řídit předpony oboru názvů.

V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , třída, která představuje názvy XML, je <xref:System.Xml.Linq.XName> . Názvy XML se často vyskytují v celém [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API a všude, kde se vyžaduje název XML, najdete <xref:System.Xml.Linq.XName> parametr. Nicméně zřídka pracujete přímo s <xref:System.Xml.Linq.XName> . <xref:System.Xml.Linq.XName>obsahuje implicitní převod z řetězce.

Další informace naleznete v tématech <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.
