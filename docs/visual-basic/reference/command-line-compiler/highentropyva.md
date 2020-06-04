---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 9501ea46eb13baa171208e20d0c9645d118c4301
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408618"
---
# <a name="-highentropyva-visual-basic"></a>-HIGHENTROPYVA (Visual Basic)
Označuje, jestli 64 spustitelný soubor nebo spustitelný soubor, který je označený parametrem [-Platform: anycpu](platform.md) , podporuje funkci náhodnosti rozložení adresního prostoru s vysokou entropií (ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Nepovinný parametr. Možnost je ve výchozím nastavení vypnutá nebo pokud zadáte `-highentropyva-` . Možnost je zapnutá, pokud zadáte `-highentropyva` nebo `-highentropyva+` .  
  
## <a name="remarks"></a>Poznámky  
 Zadáte-li tuto možnost, kompatibilní verze jádra systému Windows mohou používat vyšší stupně entropie v případě, že jádro v rámci procesu ASLR náhodné rozložení adresního prostoru. Pokud jádro používá vyšší stupně entropie, je možné přidělit větší počet adres do oblastí paměti, jako jsou zásobníky a haldy. V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.  
  
 Když je tato možnost zapnutá, cílový spustitelný soubor a všechny moduly, na kterých závisí, musí být schopné zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), když tyto moduly běží jako 64 procesy.  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
