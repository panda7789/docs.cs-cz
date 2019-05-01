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
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051699"
---
# <a name="-filealign"></a>-filealign
Určuje, kam chcete zarovnat oddíly výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Povinný parametr. Hodnota, která určuje zarovnání oddílů v souboru výstupu. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `-filealign` možnost určení zarovnání oddílů ve výstupním souboru. Oddíly jsou bloky souvislé paměti v souboru Portable Executable (PE), který obsahuje kód nebo data. `-filealign` Možnost umožňuje zkompilovat aplikaci s nestandardní zarovnání; není potřeba tuto možnost použijte, Většina vývojářů.  
  
 Každý oddíl je zarovnáno na hranici, která je násobkem `-filealign` hodnotu. Neexistuje žádná pevná výchozí hodnota. Pokud `-filealign` není zadán, kompilátor zvolí výchozí v době kompilace.  
  
 Tak, že určíte velikost oddílu, můžete změnit velikost výstupního souboru. Změna velikosti oddílu může být užitečné pro programy, které poběží na menších zařízeních.  
  
> [!NOTE]
>  `-filealign` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
