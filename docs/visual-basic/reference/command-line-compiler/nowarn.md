---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 37851f99eb88543e939ce48995ded41958e57cc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397485"
---
# <a name="-nowarn"></a>-nowarn
Potlačí schopnost kompilátoru generovat upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`numberList`|Nepovinný parametr. Čárkami oddělený seznam čísel ID upozornění, které by měl kompilátor potlačit. Nejsou-li ID upozornění zadána, budou potlačena všechna upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 `-nowarn`Možnost způsobí, že kompilátor negeneruje upozornění. Chcete-li potlačit jednotlivá upozornění, zadejte ID upozornění pro `-nowarn` parametr za dvojtečkou. Více čísel upozornění oddělte čárkami.  
  
 Je nutné zadat pouze číselnou část identifikátoru upozornění. Například pokud chcete potlačit BC42024, upozornění pro nepoužívané místní proměnné, zadejte `-nowarn:42024` .  
  
 Další informace o číslech ID upozornění najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Nastavení-upozornění v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. Zaškrtnutím políčka **Zakázat všechna upozornění** zakážete všechna upozornění.<br />     - nebo -<br />     Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu vedle upozornění.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazuje žádná upozornění.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazuje upozornění pro nepoužité místní proměnné (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
