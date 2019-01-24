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
ms.openlocfilehash: d079441e91ff90bcc974564bbd7069e0548a7d77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575287"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="12b04-102">-preferreduilang (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="12b04-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="12b04-103">S použitím `-preferreduilang` – možnost kompilátoru, můžete určit jazyk, ve kterém kompilátor jazyka C# se zobrazí výstup, jako je například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="12b04-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12b04-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="12b04-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="12b04-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="12b04-106">[Název jazyka](/windows/desktop/Intl/language-names) jazyka pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="12b04-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b04-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12b04-107">Remarks</span></span>  
 <span data-ttu-id="12b04-108">Můžete použít `-preferreduilang` – možnost kompilátoru k určení jazyk, ve kterém chcete, aby kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="12b04-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="12b04-109">Pokud není nainstalována jazyková sada pro jazyk, místo ní nastavení jazyka operačního systému a hlášené žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="12b04-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="12b04-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12b04-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b04-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12b04-111">See also</span></span>

- [<span data-ttu-id="12b04-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="12b04-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
