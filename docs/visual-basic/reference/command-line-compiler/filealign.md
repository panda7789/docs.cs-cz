---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a>/filealign
Určuje, kde chcete-li zarovnat na části výstupní soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Požadováno. Hodnota, která určuje zarovnání oddílů, které jsou ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 až 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `/filealign` možnost určení zarovnání oddílů, které jsou ve výstupním souboru. Oddíly jsou bloky souvislé paměti v souboru přenosné spustitelný soubor (PE), který obsahuje kód nebo data. `/filealign` Možnost umožňuje kompilovat vaší aplikace pomocí nestandardní zarovnání; není nutné tuto možnost použijte, Většina vývojářů.  
  
 Každá část je zarovnán na hranici, která je násobkem `/filealign` hodnotu. Neexistuje žádná pevná výchozí hodnota. Pokud `/filealign` není zadán, kompilátor zvolí výchozí v době kompilace.  
  
 Zadáním velikost oddílu, můžete změnit velikost výstupního souboru. Změna velikosti oddílu může být užitečné pro programy, které se spustí na menší zařízení.  
  
> [!NOTE]
>  `/filealign` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
