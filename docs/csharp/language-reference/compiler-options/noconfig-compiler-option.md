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
ms.openlocfilehash: 96321de5982a79cb073b658a84e0e580dd466539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (možnosti kompilátoru C#)
**- Noconfig** říká kompilátoru nechcete kompilovat bez souboru csc.rsp, který je umístěn a načíst ze stejného adresáře jako soubor csc.exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc.rsp odkazuje všechna sestavení součástí rozhraní .NET Framework. Skutečné odkazy, které zahrnuje vývojového prostředí sady Visual Studio .NET závisí na typu projektu.  
  
 Můžete upravit soubor csc.rsp a určit další kompilátoru možnosti, které mají být zahrnuty v každé kompilaci z příkazového řádku pomocí csc.exe (s výjimkou **- noconfig** možnost).  
  
 Kompilátor zpracovává možnosti předaný **csc** poslední příkaz. Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru csc.rsp.  
  
 Pokud nechcete, aby kompilátoru vyhledejte a použijte nastavení v souboru csc.rsp, zadejte **- noconfig**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
