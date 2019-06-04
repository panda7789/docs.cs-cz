---
title: 'Postupy: Vytvoření LINQ to XML Příklady (C#)'
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 116f708eb18d642cbe914cea1ea44bd1833f2af6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486060"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="ebca3-102">Postupy: Vytvoření LINQ to XML Příklady (C#)</span><span class="sxs-lookup"><span data-stu-id="ebca3-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="ebca3-103">Různé fragmenty kódu a příklady v této dokumentaci použít třídy a typy z různých oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="ebca3-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="ebca3-104">Při kompilaci kódu jazyka C#, je třeba zadat odpovídající `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="ebca3-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebca3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebca3-105">Example</span></span>  
 <span data-ttu-id="ebca3-106">Následující kód obsahuje `using` direktivy, které vyžadují příklady jazyka C# k vytvoření a spuštění.</span><span class="sxs-lookup"><span data-stu-id="ebca3-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="ebca3-107">Ne všechny `using` direktivy jsou požadovány pro každý příklad.</span><span class="sxs-lookup"><span data-stu-id="ebca3-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebca3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebca3-108">See also</span></span>

- [<span data-ttu-id="ebca3-109">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="ebca3-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
