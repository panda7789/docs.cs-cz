---
title: 'Postupy: vytvoření LINQ to XML Příklady (C#)'
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: da0d85db22de6bcb2038cbe0608983d39bd66383
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661227"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="77029-102">Postupy: vytvoření LINQ to XML Příklady (C#)</span><span class="sxs-lookup"><span data-stu-id="77029-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="77029-103">Různé fragmenty kódu a příklady v této dokumentaci použít třídy a typy z různých oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="77029-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="77029-104">Při kompilaci kódu jazyka C#, je třeba zadat odpovídající `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="77029-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77029-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="77029-105">Example</span></span>  
 <span data-ttu-id="77029-106">Následující kód obsahuje `using` direktivy, které vyžadují příklady jazyka C# k vytvoření a spuštění.</span><span class="sxs-lookup"><span data-stu-id="77029-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="77029-107">Ne všechny `using` direktivy jsou požadovány pro každý příklad.</span><span class="sxs-lookup"><span data-stu-id="77029-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77029-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="77029-108">See Also</span></span>

- [<span data-ttu-id="77029-109">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="77029-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
