---
title: Převod datových typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: d8b60428bc129958355ce5b285662847e9e712c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282412"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="ac064-102">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="ac064-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="ac064-103">Většina metod nalezených ve třídě **XmlConvert** slouží k převodu dat mezi řetězci a formátů silného typu.</span><span class="sxs-lookup"><span data-stu-id="ac064-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="ac064-104">Metody jsou nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="ac064-104">Methods are locale independent.</span></span> <span data-ttu-id="ac064-105">To znamená, že při konverzi neberou v úvahu žádná nastavení národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="ac064-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="ac064-106">Čtení řetězce jako typů</span><span class="sxs-lookup"><span data-stu-id="ac064-106">Reading String as types</span></span>  
 <span data-ttu-id="ac064-107">Následující příklad přečte řetězec a převede ho na typ **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="ac064-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="ac064-108">S ohledem na následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="ac064-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="ac064-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="ac064-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="ac064-110">Tento kód převede řetězec na formát **data a času** :</span><span class="sxs-lookup"><span data-stu-id="ac064-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="ac064-111">Zápis řetězců jako typů</span><span class="sxs-lookup"><span data-stu-id="ac064-111">Writing Strings as types</span></span>  
 <span data-ttu-id="ac064-112">Následující příklad přečte typ **Int32** a převede ho na řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac064-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="ac064-113">S ohledem na následující vstup XML:</span><span class="sxs-lookup"><span data-stu-id="ac064-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="ac064-114">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="ac064-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="ac064-115">Tento kód převede typ **Int32** na **řetězec**:</span><span class="sxs-lookup"><span data-stu-id="ac064-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac064-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac064-116">See also</span></span>

- [<span data-ttu-id="ac064-117">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ac064-117">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="ac064-118">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="ac064-118">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
