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
ms.openlocfilehash: b689a4bf0d8a1e57bf36f8ded7f2c9308f241670
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527300"
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
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
