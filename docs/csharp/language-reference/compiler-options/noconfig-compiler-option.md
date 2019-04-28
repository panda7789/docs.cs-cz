---
title: -noconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662683"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (možnosti kompilátoru C#)
**- Noconfig** přikáže kompilátoru, aby kompilovat s csc.rsp soubor, který je umístěn a načten ze stejného adresáře jako soubor csc.exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc.rsp odkazuje na všechna sestavení, které jsou součástí rozhraní .NET Framework. Skutečné odkazy, které zahrnují vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.  
  
 Můžete upravit soubor csc.rsp a určit další možnosti kompilátoru, které by měl být součástí každé kompilaci z příkazového řádku pomocí csc.exe (s výjimkou **- noconfig** možnost).  
  
 Kompilátor zpracovává možnosti předané **csc** poslední příkaz. Proto všechny možnost na příkazovém řádku přepíše nastavení stejná možnost v souboru csc.rsp.  
  
 Pokud nechcete, aby kompilátor hledal a použijte nastavení v souboru csc.rsp, zadejte **- noconfig**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
