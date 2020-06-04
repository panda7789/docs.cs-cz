---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408572"
---
# <a name="-keyfile"></a>-keyfile
Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.  
  
## <a name="syntax"></a>Syntaxe  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Povinná hodnota. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu sestavení a pak podepíše konečné sestavení pomocí privátního klíče. Chcete-li vygenerovat soubor klíče, zadejte do `sn -k file` příkazového řádku. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module` , název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](addmodule.md).  
  
 Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](keycontainer.md). Použijte [-delaysign](delaysign.md) , pokud chcete použít částečně podepsané sestavení.  
  
 Tuto možnost lze také zadat jako vlastní atribut ( <xref:System.Reflection.AssemblyKeyFileAttribute> ) ve zdrojovém kódu pro libovolný modul Microsoft Intermediate Language.  
  
 V případě `-keyfile` , že jsou zadány oba a [-](keycontainer.md) klíčové pole (buď parametr příkazového řádku nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíčů. Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, pokusí se o soubor zadaný pomocí `-keyfile` . Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako `sn -i` ), takže při další kompilaci bude kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> Tato `-keyfile` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód zkompiluje zdrojový soubor `Input.vb` a určí soubor klíče.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Reference (Visual Basic)](reference.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
