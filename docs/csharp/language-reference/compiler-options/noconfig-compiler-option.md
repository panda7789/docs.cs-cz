---
description: -unconfig (možnosti kompilátoru C#)
title: -unconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 26d0680743ccc3af26a0e81eeec9cd2fc0d693af
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125225"
---
# <a name="-noconfig-c-compiler-options"></a>-unconfig (možnosti kompilátoru C#)
Možnost **-inconfig** instruuje kompilátor, že není zkompilován se souborem CSc. rsp, který je umístěn v a načten ze stejného adresáře jako soubor csc.exe.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor csc. rsp odkazuje na všechna sestavení odeslaná pomocí .NET Framework. Skutečné odkazy, které obsahuje vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.  
  
 Můžete upravit soubor csc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace z příkazového řádku s csc.exe (kromě možnosti **--config** ).  
  
 Kompilátor zpracuje možnosti předané do příkazu **CSC** jako poslední. Proto všechny možnosti příkazového řádku přepisují nastavení stejné možnosti v souboru CSc. rsp.  
  
 Pokud nechcete, aby kompilátor hledal a použil nastavení v souboru CSc. rsp, zadejte **-inconfig**.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
