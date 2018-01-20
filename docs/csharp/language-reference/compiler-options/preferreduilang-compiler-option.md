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
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="1cc95-102">-preferreduilang (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1cc95-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="1cc95-103">Pomocí `-preferreduilang` – možnost kompilátoru, můžete zadat jazyk, ve kterém kompilátor jazyka C# zobrazí výstup, jako je například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="1cc95-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cc95-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="1cc95-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1cc95-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="1cc95-106">[Název jazyka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) jazyka, který chcete použít pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1cc95-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cc95-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1cc95-107">Remarks</span></span>  
 <span data-ttu-id="1cc95-108">Můžete použít `-preferreduilang` – možnost kompilátoru zadat jazyk, který chcete kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1cc95-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="1cc95-109">Pokud není nainstalována sada language pack pro jazyk, bude místo něj použita na jazyková nastavení operačního systému a žádná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="1cc95-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="1cc95-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cc95-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc95-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cc95-111">See Also</span></span>  
 [<span data-ttu-id="1cc95-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1cc95-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
