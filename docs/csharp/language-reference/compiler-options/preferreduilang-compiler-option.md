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
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (možnosti kompilátoru C#)
Pomocí `-preferreduilang` – možnost kompilátoru, můžete zadat jazyk, ve kterém kompilátor jazyka C# zobrazí výstup, jako je například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Název jazyka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) jazyka, který chcete použít pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `-preferreduilang` – možnost kompilátoru zadat jazyk, který chcete kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku. Pokud není nainstalována sada language pack pro jazyk, bude místo něj použita na jazyková nastavení operačního systému a žádná chybová zpráva.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
