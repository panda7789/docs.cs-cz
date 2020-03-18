---
title: -preferreduilang (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602556"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="8b545-102">-preferreduilang (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8b545-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="8b545-103">Pomocí možnosti `-preferreduilang` kompilátoru můžete určit jazyk, ve kterém kompilátor Jazyka C# zobrazuje výstup, například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="8b545-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b545-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b545-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b545-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8b545-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="8b545-106">[Název jazyka,](/windows/desktop/Intl/language-names) který se má použít pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8b545-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b545-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b545-107">Remarks</span></span>  
 <span data-ttu-id="8b545-108">Pomocí možnosti `-preferreduilang` kompilátoru můžete určit jazyk, který má kompilátor Jazyka C# použít pro chybové zprávy a další výstup příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8b545-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="8b545-109">Pokud jazyková sada pro jazyk není nainstalována, místo toho se použije nastavení jazyka operačního systému a není hlášena žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="8b545-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="8b545-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b545-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b545-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b545-111">See also</span></span>

- [<span data-ttu-id="8b545-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b545-112">C# Compiler Options</span></span>](./index.md)
