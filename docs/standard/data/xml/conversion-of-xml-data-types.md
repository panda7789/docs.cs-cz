---
title: "Převod XML datových typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="bd445-102">Převod XML datových typů</span><span class="sxs-lookup"><span data-stu-id="bd445-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="bd445-103">Většina metody nalezen v **XmlConvert** třída slouží k převodu dat mezi řetězci a formáty silného typu.</span><span class="sxs-lookup"><span data-stu-id="bd445-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="bd445-104">Metody jsou nezávislé národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="bd445-104">Methods are locale independent.</span></span> <span data-ttu-id="bd445-105">To znamená, že není berou v úvahu žádné nastavení národního prostředí při provádění převod.</span><span class="sxs-lookup"><span data-stu-id="bd445-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="bd445-106">Čtení řetězec jako typy</span><span class="sxs-lookup"><span data-stu-id="bd445-106">Reading String as types</span></span>  
 <span data-ttu-id="bd445-107">Následující příklad načte řetězec a převede jej na **data a času** typu.</span><span class="sxs-lookup"><span data-stu-id="bd445-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="bd445-108">Zadané následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="bd445-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="bd445-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="bd445-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="bd445-110">Převede řetězec na tento kód **data a času** formátu:</span><span class="sxs-lookup"><span data-stu-id="bd445-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="bd445-111">Zápis řetězců jako typy</span><span class="sxs-lookup"><span data-stu-id="bd445-111">Writing Strings as types</span></span>  
 <span data-ttu-id="bd445-112">Následující ukázkové čtení **Int32** a převede jej na řetězec.</span><span class="sxs-lookup"><span data-stu-id="bd445-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="bd445-113">Zadané následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="bd445-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="bd445-114">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="bd445-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="bd445-115">Převede tento kód **Int32** do **řetězec**:</span><span class="sxs-lookup"><span data-stu-id="bd445-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd445-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd445-116">See Also</span></span>  
 [<span data-ttu-id="bd445-117">Převádění řetězců na rozhraní .NET Framework datové typy</span><span class="sxs-lookup"><span data-stu-id="bd445-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="bd445-118">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="bd445-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
