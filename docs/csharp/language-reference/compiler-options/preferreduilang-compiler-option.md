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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang – (možnosti kompilátoru C#)
Pomocí `-preferreduilang` Možnosti kompilátoru lze určit jazyk, ve kterém kompilátor jazyka C# zobrazuje výstup, například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Název jazyka](/windows/desktop/Intl/language-names) jazyka, který má být použit pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `-preferreduilang` Možnosti kompilátoru můžete určit jazyk, který má kompilátor C# použít pro chybové zprávy a další výstup z příkazového řádku. Pokud není nainstalovaná jazyková sada pro jazyk, místo toho se použije jazykové nastavení operačního systému a neohlásí se žádná chyba.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
