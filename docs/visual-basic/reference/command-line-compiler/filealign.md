---
title: -filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a>-filealign
Určuje, kde chcete-li zarovnat na části výstupní soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Požadováno. Hodnota, která určuje zarovnání oddílů, které jsou ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 až 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `-filealign` možnost určení zarovnání oddílů, které jsou ve výstupním souboru. Oddíly jsou bloky souvislé paměti v souboru přenosné spustitelný soubor (PE), který obsahuje kód nebo data. `-filealign` Možnost umožňuje kompilovat vaší aplikace pomocí nestandardní zarovnání; není nutné tuto možnost použijte, Většina vývojářů.  
  
 Každá část je zarovnán na hranici, která je násobkem `-filealign` hodnotu. Neexistuje žádná pevná výchozí hodnota. Pokud `-filealign` není zadán, kompilátor zvolí výchozí v době kompilace.  
  
 Zadáním velikost oddílu, můžete změnit velikost výstupního souboru. Změna velikosti oddílu může být užitečné pro programy, které se spustí na menší zařízení.  
  
> [!NOTE]
>  `-filealign` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
