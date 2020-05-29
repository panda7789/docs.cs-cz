---
title: Převod datových typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b6e6f2c4b28e9220727bf0fe1a958a7b69111571
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202164"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="0ee68-102">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="0ee68-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="0ee68-103">Většina metod nalezených ve třídě **XmlConvert** slouží k převodu dat mezi řetězci a formátů silného typu.</span><span class="sxs-lookup"><span data-stu-id="0ee68-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="0ee68-104">Metody jsou nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="0ee68-104">Methods are locale independent.</span></span> <span data-ttu-id="0ee68-105">To znamená, že při konverzi neberou v úvahu žádná nastavení národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="0ee68-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="0ee68-106">Čtení řetězce jako typů</span><span class="sxs-lookup"><span data-stu-id="0ee68-106">Reading String as types</span></span>  
 <span data-ttu-id="0ee68-107">Následující příklad přečte řetězec a převede ho na typ **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="0ee68-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="0ee68-108">S ohledem na následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="0ee68-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="0ee68-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="0ee68-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="0ee68-110">Tento kód převede řetězec na formát **data a času** :</span><span class="sxs-lookup"><span data-stu-id="0ee68-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="0ee68-111">Zápis řetězců jako typů</span><span class="sxs-lookup"><span data-stu-id="0ee68-111">Writing Strings as types</span></span>  
 <span data-ttu-id="0ee68-112">Následující příklad přečte typ **Int32** a převede ho na řetězec.</span><span class="sxs-lookup"><span data-stu-id="0ee68-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="0ee68-113">S ohledem na následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="0ee68-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="0ee68-114">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="0ee68-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="0ee68-115">Tento kód převede typ **Int32** na **řetězec**:</span><span class="sxs-lookup"><span data-stu-id="0ee68-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ee68-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ee68-116">See also</span></span>

- [<span data-ttu-id="0ee68-117">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ee68-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="0ee68-118">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="0ee68-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
