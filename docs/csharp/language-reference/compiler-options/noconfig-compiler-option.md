---
title: -unconfig (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602735"
---
# <a name="-noconfig-c-compiler-options"></a>-unconfig (C# možnosti kompilátoru)
Možnost **-inconfig** říká kompilátoru, že není zkompilován se souborem CSc. rsp, který je umístěn v a načten ze stejného adresáře jako soubor csc. exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc. rsp odkazuje na všechna sestavení odeslaná pomocí .NET Framework. Skutečné odkazy, které obsahuje vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.  
  
 Můžete upravit soubor csc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty v každé kompilaci z příkazového řádku pomocí CSc. exe (kromě možnosti **---config** ).  
  
 Kompilátor zpracuje možnosti předané do příkazu **CSC** jako poslední. Proto všechny možnosti příkazového řádku přepisují nastavení stejné možnosti v souboru CSc. rsp.  
  
 Pokud nechcete, aby kompilátor hledal a použil nastavení v souboru CSc. rsp, zadejte **-inconfig**.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
