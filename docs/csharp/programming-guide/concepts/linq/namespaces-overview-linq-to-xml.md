---
title: Přehled názvových prostorů (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d4c43a407921e1a74d1792f7cae4e320ca1234c0
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709899"
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled názvových prostorů (LINQ to XML)

Tento článek představuje obory názvů <xref:System.Xml.Linq.XName> , třídu <xref:System.Xml.Linq.XNamespace> a třídu.
  
## <a name="xml-names"></a>Názvy XML  

Názvy XML jsou často zdrojem složitosti při programování XML. Název XML se skládá z oboru názvů XML (označuje se také jako identifikátor URI oboru názvů XML) a místního názvu. Obor názvů XML je podobný oboru názvů v programu založeném na .NET Framework. Umožňuje jednoznačně kvalifikovat názvy elementů a atributů. To pomáhá zabránit konfliktu názvů mezi různými částmi dokumentu XML. Pokud jste deklarovali obor názvů XML, můžete vybrat místní název, který musí být v rámci tohoto oboru názvů jedinečný.  
  
Dalším aspektem názvů XML jsou *předpony oboru názvů*XML. Předpony XML způsobují většinu složitosti názvů XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, díky čemuž je dokument XML výstižnější a srozumitelný. Předpony XML jsou však závislé na jejich kontextu a mají význam, což zvyšuje složitost. Předpona `aw` XML může být například přidružena k jednomu oboru názvů XML v jedné části stromu XML a s jiným oborem názvů XML v jiné části stromu XML.  
  
Jednou z výhod použití nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] C# je, že nemusíte používat předpony XML. Při [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načítání nebo analýze dokumentu XML je každá předpona XML přeložena na odpovídající obor názvů XML. Po tom, když pracujete s dokumentem, který používá obory názvů, skoro vždy získáte přístup k oborům názvů prostřednictvím identifikátoru URI oboru názvů a nikoli prostřednictvím předpony oboru názvů. Když vývojáři pracují s názvy XML v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , vždy pracují s plně kvalifikovaným názvem XML (tj. obor názvů XML a místní název). V případě potřeby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ale umožňuje pracovat s a řídit předpony oboru názvů.  
  
V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], třída, která představuje názvy XML, <xref:System.Xml.Linq.XName>je. Názvy XML se často vyskytují v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] celém rozhraní API a všude, kde se vyžaduje název XML, <xref:System.Xml.Linq.XName> najdete parametr. Nicméně zřídka pracujete přímo s <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>obsahuje implicitní převod z řetězce.  
  
Další informace naleznete v tématu <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.