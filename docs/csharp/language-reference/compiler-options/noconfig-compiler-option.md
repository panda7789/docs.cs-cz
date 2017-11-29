---
title: "-noconfig (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2b15853cdd6ee9fe12b8b3ba3388a74e49c9701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig-c-compiler-options"></a>/noconfig (Možnosti kompilátoru C#)
**/Noconfig** říká kompilátoru nechcete kompilovat bez souboru csc.rsp, který je umístěn a načíst ze stejného adresáře jako soubor csc.exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc.rsp odkazuje všechna sestavení součástí rozhraní .NET Framework. Skutečné odkazy, které zahrnuje vývojového prostředí sady Visual Studio .NET závisí na typu projektu.  
  
 Můžete upravit soubor csc.rsp a určit další kompilátoru možnosti, které mají být zahrnuty v každé kompilaci z příkazového řádku pomocí csc.exe (s výjimkou **/noconfig** možnost).  
  
 Kompilátor zpracovává možnosti předaný **csc** poslední příkaz. Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru csc.rsp.  
  
 Pokud nechcete, aby kompilátoru vyhledejte a použijte nastavení v souboru csc.rsp, zadejte **/noconfig**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
