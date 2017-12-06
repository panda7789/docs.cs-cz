---
title: "-preferreduilang (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a96a054b3d1f73b0fee209557388f7ea213ebbe9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="preferreduilang-c-compiler-options"></a><span data-ttu-id="c12a8-102">/preferreduilang (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c12a8-102">/preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="c12a8-103">Pomocí `/preferreduilang` – možnost kompilátoru, můžete zadat jazyk, ve kterém kompilátor jazyka C# zobrazí výstup, jako je například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c12a8-103">By using the `/preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c12a8-104">Syntax</span></span>  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="c12a8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c12a8-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="c12a8-106">[Název jazyka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) jazyka, který chcete použít pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c12a8-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c12a8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c12a8-107">Remarks</span></span>  
 <span data-ttu-id="c12a8-108">Můžete použít `/preferreduilang` – možnost kompilátoru zadat jazyk, který chcete kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c12a8-108">You can use the `/preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="c12a8-109">Pokud není nainstalována sada language pack pro jazyk, bude místo něj použita na jazyková nastavení operačního systému a žádná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="c12a8-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="c12a8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c12a8-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12a8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c12a8-111">See Also</span></span>  
 [<span data-ttu-id="c12a8-112">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="c12a8-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
