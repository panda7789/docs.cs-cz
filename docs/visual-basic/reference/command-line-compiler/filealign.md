---
title: -filealign
ms.date: 03/10/2018
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
ms.openlocfilehash: cf9c854060e5254cedc6c1004ac3e4f25fbdbbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650664"
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
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
