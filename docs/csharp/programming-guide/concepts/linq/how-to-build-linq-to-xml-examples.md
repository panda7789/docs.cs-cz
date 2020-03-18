---
title: Jak vytvořit LINQ na XML příklady (C#)
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 289a13daed7e3c871156bf50c6fa04c113c0cd13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141464"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="b7941-102">Jak vytvořit LINQ na XML příklady (C#)</span><span class="sxs-lookup"><span data-stu-id="b7941-102">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="b7941-103">Různé úryvky a příklady v této dokumentaci používají třídy a typy z různých oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="b7941-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="b7941-104">Při kompilaci kódu Jazyka C# je `using` třeba zadat příslušné direktivy.</span><span class="sxs-lookup"><span data-stu-id="b7941-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7941-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7941-105">Example</span></span>  
 <span data-ttu-id="b7941-106">Následující kód obsahuje `using` direktivy, které c# příklady vyžadují k sestavení a spuštění.</span><span class="sxs-lookup"><span data-stu-id="b7941-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="b7941-107">Ne `using` všechny direktivy jsou vyžadovány pro každý příklad.</span><span class="sxs-lookup"><span data-stu-id="b7941-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7941-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7941-108">See also</span></span>

- [<span data-ttu-id="b7941-109">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7941-109">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
