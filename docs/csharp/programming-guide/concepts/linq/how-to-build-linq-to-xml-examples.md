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
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="bebf3-103">Postup sestavení příkladů LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bebf3-103">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="bebf3-104">Jednotlivé fragmenty kódu a příklady v této dokumentaci využívají třídy a typy z různých oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="bebf3-104">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="bebf3-105">Při kompilování kódu jazyka C# je nutné dodat příslušné `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="bebf3-105">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bebf3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bebf3-106">Example</span></span>  
 <span data-ttu-id="bebf3-107">Následující kód obsahuje `using` direktivy, které příklady jazyka C# vyžadují pro sestavení a spuštění.</span><span class="sxs-lookup"><span data-stu-id="bebf3-107">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="bebf3-108">Ne všechny `using` direktivy jsou požadovány pro každý příklad.</span><span class="sxs-lookup"><span data-stu-id="bebf3-108">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bebf3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="bebf3-109">See also</span></span>

- [<span data-ttu-id="bebf3-110">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bebf3-110">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
