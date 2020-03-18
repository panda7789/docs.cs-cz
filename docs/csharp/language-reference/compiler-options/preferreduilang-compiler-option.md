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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (Možnosti kompilátoru Jazyka C#)
Pomocí možnosti `-preferreduilang` kompilátoru můžete určit jazyk, ve kterém kompilátor Jazyka C# zobrazuje výstup, například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Název jazyka,](/windows/desktop/Intl/language-names) který se má použít pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí možnosti `-preferreduilang` kompilátoru můžete určit jazyk, který má kompilátor Jazyka C# použít pro chybové zprávy a další výstup příkazového řádku. Pokud jazyková sada pro jazyk není nainstalována, místo toho se použije nastavení jazyka operačního systému a není hlášena žádná chyba.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
