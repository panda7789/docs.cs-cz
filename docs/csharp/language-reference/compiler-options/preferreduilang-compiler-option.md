---
title: "-preferreduilang (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a96a054b3d1f73b0fee209557388f7ea213ebbe9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (Možnosti kompilátoru C#)
Pomocí `/preferreduilang` – možnost kompilátoru, můžete zadat jazyk, ve kterém kompilátor jazyka C# zobrazí výstup, jako je například chybové zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Název jazyka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) jazyka, který chcete použít pro výstup kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `/preferreduilang` – možnost kompilátoru zadat jazyk, který chcete kompilátor jazyka C# pro chybové zprávy a další výstup příkazového řádku. Pokud není nainstalována sada language pack pro jazyk, bude místo něj použita na jazyková nastavení operačního systému a žádná chybová zpráva.  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)
