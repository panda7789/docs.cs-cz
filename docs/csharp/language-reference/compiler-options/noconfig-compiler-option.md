---
title: -noconfig (Možnosti kompilátoru Jazyka C#)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602735"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (Možnosti kompilátoru Jazyka C#)
Možnost **-noconfig** říká kompilátoru, aby nekompiloval se souborem csc.rsp, který je umístěn a načten ze stejného adresáře jako soubor csc.exe.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc.rsp odkazuje na všechna sestavení dodávaná s rozhraním .NET Framework. Skutečné odkazy, které obsahuje vývojové prostředí Visual Studio .NET, závisí na typu projektu.  
  
 Můžete upravit soubor csc.rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace z příkazového řádku s csc.exe (kromě volby **-noconfig).**  
  
 Kompilátor zpracuje možnosti předané příkazu **csc** jako poslední. Proto všechny možnosti na příkazovém řádku přepíše nastavení stejné volby v souboru csc.rsp.  
  
 Pokud nechcete, aby kompilátor vyhledává a používal nastavení v souboru csc.rsp, zadejte **-noconfig**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
