---
title: Konstanty (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b91f2a749557f94a68f1929d649824719160d9ee
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786965"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="b1a8f-102">Konstanty (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b1a8f-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="b1a8f-103">Toto téma popisuje typ jazyka, dodavatele jazyka a konstanty typu dokumentu, které jsou definovány v souboru CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="b1a8f-104">Konstanty typu jazyka</span><span class="sxs-lookup"><span data-stu-id="b1a8f-104">Language Type Constants</span></span>  
 <span data-ttu-id="b1a8f-105">V následující tabulce jsou uvedeny konstanty typu jazyka, které reprezentují identifikátory GUID, které identifikují programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="b1a8f-106">Písmeno</span><span class="sxs-lookup"><span data-stu-id="b1a8f-106">Symbol</span></span>|<span data-ttu-id="b1a8f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1a8f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1a8f-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="b1a8f-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="b1a8f-109">Určuje jazyk C.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="b1a8f-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="b1a8f-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="b1a8f-111">Určuje C++ jazyk.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="b1a8f-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="b1a8f-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="b1a8f-113">Určuje C# jazyk.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="b1a8f-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="b1a8f-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="b1a8f-115">Označuje základní jazyk.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="b1a8f-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="b1a8f-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="b1a8f-117">Označuje jazyk Java.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="b1a8f-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="b1a8f-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="b1a8f-119">Určuje jazyk COBOL.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="b1a8f-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="b1a8f-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="b1a8f-121">Určuje jazyk Pascal.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="b1a8f-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="b1a8f-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="b1a8f-123">Označuje kód sestavení jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="b1a8f-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="b1a8f-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="b1a8f-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="b1a8f-125">Určuje jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="b1a8f-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="b1a8f-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="b1a8f-127">Označuje jazyk SMC.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="b1a8f-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="b1a8f-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="b1a8f-129">Určuje C++ jazyk povolený pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="b1a8f-130">Konstanty dodavatele jazyka</span><span class="sxs-lookup"><span data-stu-id="b1a8f-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="b1a8f-131">V následující tabulce jsou uvedeny konstanty dodavatelů jazyka, které reprezentují identifikátory GUID, které identifikují dodavatele programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="b1a8f-132">Písmeno</span><span class="sxs-lookup"><span data-stu-id="b1a8f-132">Symbol</span></span>|<span data-ttu-id="b1a8f-133">Popis</span><span class="sxs-lookup"><span data-stu-id="b1a8f-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1a8f-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="b1a8f-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="b1a8f-135">Označuje Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="b1a8f-136">Konstanty typu dokumentu</span><span class="sxs-lookup"><span data-stu-id="b1a8f-136">Document Type Constants</span></span>  
 <span data-ttu-id="b1a8f-137">V následující tabulce jsou uvedeny konstanty typu dokumentu, které reprezentují identifikátory GUID, které identifikují typy dokumentů.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="b1a8f-138">Písmeno</span><span class="sxs-lookup"><span data-stu-id="b1a8f-138">Symbol</span></span>|<span data-ttu-id="b1a8f-139">Popis</span><span class="sxs-lookup"><span data-stu-id="b1a8f-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1a8f-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="b1a8f-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="b1a8f-141">Označuje textový dokument.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="b1a8f-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="b1a8f-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="b1a8f-143">Indikuje, že dokument není typu text.</span><span class="sxs-lookup"><span data-stu-id="b1a8f-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1a8f-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1a8f-144">See also</span></span>

- [<span data-ttu-id="b1a8f-145">Referenční informace o nespravovaném rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b1a8f-145">Unmanaged API Reference</span></span>](index.md)
