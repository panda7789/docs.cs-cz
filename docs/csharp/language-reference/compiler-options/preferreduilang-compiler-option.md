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
ms.openlocfilehash: a1fbbb8415e5e3405f039489aa071b0624065a9d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530140"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="5ef8b-102">-preferreduilang (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5ef8b-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="5ef8b-103">S použitím `-preferreduilang` – možnost kompilátoru, můžete určit jazyk, ve kterém kompilátor jazyka C# se zobrazí výstup, jako je například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ef8b-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ef8b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5ef8b-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="5ef8b-106">[Název jazyka](/windows/desktop/Intl/language-names) jazyka pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef8b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ef8b-107">Remarks</span></span>  
 <span data-ttu-id="5ef8b-108">Můžete použít `-preferreduilang` – možnost kompilátoru k určení jazyk, ve kterém chcete, aby kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="5ef8b-109">Pokud není nainstalována jazyková sada pro jazyk, místo ní nastavení jazyka operačního systému a hlášené žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="5ef8b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ef8b-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef8b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ef8b-111">See Also</span></span>

- [<span data-ttu-id="5ef8b-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ef8b-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
