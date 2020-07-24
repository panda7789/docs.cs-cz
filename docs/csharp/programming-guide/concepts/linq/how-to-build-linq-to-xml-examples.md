---
title: Postup sestavení příkladů LINQ to XML (C#)
description: Poskytněte příslušné direktivy using, které jsou potřebné pro zkompilování jazyka C# ke spuštění poskytnutých fragmentů a příkladů LINQ to XML.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: f54944dcb68e1fd7d00f37c9c5381f345efc820e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103592"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a>Postup sestavení příkladů LINQ to XML (C#)
Jednotlivé fragmenty kódu a příklady v této dokumentaci využívají třídy a typy z různých oborů názvů. Při kompilování kódu jazyka C# je nutné dodat příslušné `using` direktivy.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje `using` direktivy, které příklady jazyka C# vyžadují pro sestavení a spuštění. Ne všechny `using` direktivy jsou požadovány pro každý příklad.  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
