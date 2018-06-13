---
title: -preferreduilang (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211748"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="b94f4-102">-preferreduilang (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b94f4-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="b94f4-103">Pomocí `-preferreduilang` – možnost kompilátoru, můžete zadat jazyk, ve kterém kompilátor jazyka C# zobrazí výstup, jako je například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="b94f4-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94f4-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="b94f4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b94f4-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="b94f4-106">[Název jazyka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) jazyka, který chcete použít pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b94f4-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b94f4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b94f4-107">Remarks</span></span>  
 <span data-ttu-id="b94f4-108">Můžete použít `-preferreduilang` – možnost kompilátoru zadat jazyk, který chcete kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b94f4-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="b94f4-109">Pokud není nainstalována sada language pack pro jazyk, bude místo něj použita na jazyková nastavení operačního systému a žádná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="b94f4-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="b94f4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b94f4-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94f4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b94f4-111">See Also</span></span>  
 [<span data-ttu-id="b94f4-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b94f4-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
