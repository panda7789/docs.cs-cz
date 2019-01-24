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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (možnosti kompilátoru C#)
S použitím `-preferreduilang` – možnost kompilátoru, můžete určit jazyk, ve kterém kompilátor jazyka C# se zobrazí výstup, jako je například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Název jazyka](/windows/desktop/Intl/language-names) jazyka pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `-preferreduilang` – možnost kompilátoru k určení jazyk, ve kterém chcete, aby kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku. Pokud není nainstalována jazyková sada pro jazyk, místo ní nastavení jazyka operačního systému a hlášené žádné chyby.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
