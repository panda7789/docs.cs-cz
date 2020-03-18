---
title: -fullpaths (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /fullpaths
helpviewer_keywords:
- /fullpaths compiler option [C#]
- absolute paths [C#]
- fullpaths compiler option [C#]
- full paths [C#]
- -fullpaths compiler option [C#]
ms.assetid: d2a5f857-cbb2-430b-879c-d648aaf0b8c4
ms.openlocfilehash: 3bb4027f1c479bbaedda889d72712acb587b5713
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606864"
---
# <a name="-fullpaths-c-compiler-options"></a><span data-ttu-id="23239-102">-fullpaths (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="23239-102">-fullpaths (C# Compiler Options)</span></span>
<span data-ttu-id="23239-103">Možnost **-fullpaths** způsobí, že kompilátor určí úplnou cestu k souboru při výpisu chyb kompilace a upozornění.</span><span class="sxs-lookup"><span data-stu-id="23239-103">The **-fullpaths** option causes the compiler to specify the full path to the file when listing compilation errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23239-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23239-104">Syntax</span></span>  
  
```console  
-fullpaths  
```  
  
## <a name="remarks"></a><span data-ttu-id="23239-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23239-105">Remarks</span></span>  
 <span data-ttu-id="23239-106">Ve výchozím nastavení chyby a upozornění, které vyplývají z kompilace, určují název souboru, ve kterém byla chyba nalezena.</span><span class="sxs-lookup"><span data-stu-id="23239-106">By default, errors and warnings that result from compilation specify the name of the file in which an error was found.</span></span> <span data-ttu-id="23239-107">Volba **-fullpaths** způsobí, že kompilátor určí úplnou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="23239-107">The **-fullpaths** option causes the compiler to specify the full path to the file.</span></span>  
  
 <span data-ttu-id="23239-108">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="23239-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23239-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="23239-109">See also</span></span>

- [<span data-ttu-id="23239-110">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="23239-110">C# Compiler Options</span></span>](./index.md)
