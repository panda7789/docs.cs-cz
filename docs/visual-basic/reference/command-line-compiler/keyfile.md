---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266739"
---
# <a name="-keyfile"></a>-keyfile
Určuje soubor obsahující klíč nebo pár klíčů, aby sestava byla silně pojmenujena.  
  
## <a name="syntax"></a>Syntaxe  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Povinná hodnota. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezeru, uzavřete jej do uvozovek (" ").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče. Chcete-li vygenerovat `sn -k file` soubor klíče, zadejte příkaz na příkazovém řádku. Další informace naleznete v [tématu Sn.exe (Strong Name Tool).](../../../framework/tools/sn-exe-strong-name-tool.md)  
  
 Pokud kompilujete s `-target:module`, název souboru klíče je držen v modulu a začleněny do sestavení, který je vytvořen při kompilaci sestavení s [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Můžete také předat informace o šifrování kompilátoru s [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Použijte [-delaysign,](../../../visual-basic/reference/command-line-compiler/delaysign.md) pokud chcete částečně podepsané sestavení.  
  
 Tuto možnost můžete také zadat jako<xref:System.Reflection.AssemblyKeyFileAttribute>vlastní atribut ( ) ve zdrojovém kódu pro libovolný modul zprostředkujících jazyků společnosti Microsoft.  
  
 V případě, že oba `-keyfile` a [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) jsou určeny (buď příkazového řádku možnost nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíče. Pokud se to podaří, sestavení je podepsáno informacemi v kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, pokusí se `-keyfile`o soubor zadaný . Pokud se to podaří, sestavení je podepsáno s informacemi v souboru klíče a `sn -i`informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako ) tak, aby v další kompilaci byl kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace o podepisování sestavení najdete v tématu [Vytváření a používání sestavení se silným názvem.](../../../standard/assembly/create-use-strong-named.md)  
  
> [!NOTE]
> Tato `-keyfile` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
