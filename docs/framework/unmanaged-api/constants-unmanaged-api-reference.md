---
title: "Konstanty (referenční dokumentace nespravovaného rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45e4d41c16695010dc452d2f22850d43f885974a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="ab16e-102">Konstanty (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ab16e-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="ab16e-103">Toto téma popisuje typ language, jazyk dodavatele a konstanty typu dokumentu, které jsou definovány v CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="ab16e-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="ab16e-104">Konstanty jazyka typu</span><span class="sxs-lookup"><span data-stu-id="ab16e-104">Language Type Constants</span></span>  
 <span data-ttu-id="ab16e-105">Následující tabulka uvádí jazyk typ konstanty, které představují identifikátory GUID, které identifikují programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="ab16e-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="ab16e-106">Symbol</span><span class="sxs-lookup"><span data-stu-id="ab16e-106">Symbol</span></span>|<span data-ttu-id="ab16e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ab16e-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ab16e-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="ab16e-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="ab16e-109">Určuje jazyk C.</span><span class="sxs-lookup"><span data-stu-id="ab16e-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="ab16e-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="ab16e-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="ab16e-111">Určuje jazyk C++.</span><span class="sxs-lookup"><span data-stu-id="ab16e-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="ab16e-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="ab16e-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="ab16e-113">Určuje jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="ab16e-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="ab16e-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="ab16e-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="ab16e-115">Určuje základní jazyk.</span><span class="sxs-lookup"><span data-stu-id="ab16e-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="ab16e-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="ab16e-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="ab16e-117">Určuje jazyk Java.</span><span class="sxs-lookup"><span data-stu-id="ab16e-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="ab16e-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="ab16e-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="ab16e-119">Určuje jazyk, COBOL.</span><span class="sxs-lookup"><span data-stu-id="ab16e-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="ab16e-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="ab16e-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="ab16e-121">Určuje jazyk, Pascal.</span><span class="sxs-lookup"><span data-stu-id="ab16e-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="ab16e-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="ab16e-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="ab16e-123">Určuje kód sestavení (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab16e-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="ab16e-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="ab16e-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="ab16e-125">Určuje jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="ab16e-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="ab16e-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="ab16e-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="ab16e-127">Určuje jazyk, SMC.</span><span class="sxs-lookup"><span data-stu-id="ab16e-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="ab16e-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="ab16e-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="ab16e-129">Určuje jazyk C++ povolené pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab16e-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="ab16e-130">Konstanty jazyka dodavatele</span><span class="sxs-lookup"><span data-stu-id="ab16e-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="ab16e-131">Následující tabulka uvádí konstanty dodavatele, které představují identifikátory GUID, které identifikují programovací jazyk dodavatelé jazyk.</span><span class="sxs-lookup"><span data-stu-id="ab16e-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="ab16e-132">Symbol</span><span class="sxs-lookup"><span data-stu-id="ab16e-132">Symbol</span></span>|<span data-ttu-id="ab16e-133">Popis</span><span class="sxs-lookup"><span data-stu-id="ab16e-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ab16e-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="ab16e-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="ab16e-135">Označuje společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab16e-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="ab16e-136">Konstanty typu dokumentu</span><span class="sxs-lookup"><span data-stu-id="ab16e-136">Document Type Constants</span></span>  
 <span data-ttu-id="ab16e-137">Následující tabulka uvádí dokumentu typ konstanty, které představují identifikátory GUID, které identifikují typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ab16e-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="ab16e-138">Symbol</span><span class="sxs-lookup"><span data-stu-id="ab16e-138">Symbol</span></span>|<span data-ttu-id="ab16e-139">Popis</span><span class="sxs-lookup"><span data-stu-id="ab16e-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ab16e-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="ab16e-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="ab16e-141">Určuje textový dokument.</span><span class="sxs-lookup"><span data-stu-id="ab16e-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="ab16e-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="ab16e-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="ab16e-143">Určuje jiný textový dokument.</span><span class="sxs-lookup"><span data-stu-id="ab16e-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab16e-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab16e-144">See Also</span></span>  
 [<span data-ttu-id="ab16e-145">Referenční dokumentace nespravovaného rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ab16e-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
