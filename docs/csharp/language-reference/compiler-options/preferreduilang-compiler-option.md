---
description: -preferreduilang – (možnosti kompilátoru C#)
title: -preferreduilang – (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: f68652e910651ab5c4184376d9eb7729303382d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124848"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="f34ed-103">-preferreduilang – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f34ed-103">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="f34ed-104">Pomocí `-preferreduilang` Možnosti kompilátoru lze určit jazyk, ve kterém kompilátor jazyka C# zobrazuje výstup, například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="f34ed-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34ed-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f34ed-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="f34ed-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f34ed-106">Arguments</span></span>  
 `language`  
 <span data-ttu-id="f34ed-107">[Název jazyka](/windows/desktop/Intl/language-names) jazyka, který má být použit pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f34ed-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f34ed-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f34ed-108">Remarks</span></span>  
 <span data-ttu-id="f34ed-109">Pomocí `-preferreduilang` Možnosti kompilátoru můžete určit jazyk, který má kompilátor C# použít pro chybové zprávy a další výstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f34ed-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="f34ed-110">Pokud není nainstalovaná jazyková sada pro jazyk, místo toho se použije jazykové nastavení operačního systému a neohlásí se žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="f34ed-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="f34ed-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f34ed-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34ed-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f34ed-112">See also</span></span>

- [<span data-ttu-id="f34ed-113">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="f34ed-113">C# Compiler Options</span></span>](./index.md)
