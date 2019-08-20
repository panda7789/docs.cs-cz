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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang – (C# možnosti kompilátoru)
Pomocí `-preferreduilang` možnosti kompilátoru můžete určit jazyk, ve kterém C# kompilátor zobrazuje výstup, například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Název jazyka](/windows/desktop/Intl/language-names) jazyka, který má být použit pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `-preferreduilang` možnosti kompilátoru můžete určit jazyk, který má C# kompilátor používat pro chybové zprávy a další výstup z příkazového řádku. Pokud není nainstalovaná jazyková sada pro jazyk, místo toho se použije jazykové nastavení operačního systému a neohlásí se žádná chyba.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
