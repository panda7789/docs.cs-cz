---
title: -preferreduilang – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602556"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="37645-102">-preferreduilang – (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="37645-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="37645-103">Pomocí `-preferreduilang` možnosti kompilátoru můžete určit jazyk, ve kterém C# kompilátor zobrazuje výstup, například chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="37645-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37645-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37645-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="37645-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="37645-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="37645-106">[Název jazyka](/windows/desktop/Intl/language-names) jazyka, který má být použit pro výstup kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="37645-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37645-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37645-107">Remarks</span></span>  
 <span data-ttu-id="37645-108">Pomocí `-preferreduilang` možnosti kompilátoru můžete určit jazyk, který má C# kompilátor používat pro chybové zprávy a další výstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="37645-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="37645-109">Pokud není nainstalovaná jazyková sada pro jazyk, místo toho se použije jazykové nastavení operačního systému a neohlásí se žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="37645-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="37645-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37645-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37645-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37645-111">See also</span></span>

- [<span data-ttu-id="37645-112">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="37645-112">C# Compiler Options</span></span>](./index.md)
