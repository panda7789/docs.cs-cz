---
title: -keyfile (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: eef843c87b8f1993c3419b261894a6df31096294
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606885"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# možnosti kompilátoru)
Určuje název souboru, který obsahuje kryptografický klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|----------|----------------|  
|`file`|Název souboru, který obsahuje klíč se silným názvem.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití této možnosti kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Chcete-li vygenerovat soubor klíče, zadejte do `file` příkazového řádku SN-k.  
  
 Pokud kompilujete pomocí **-target: Module**, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](./addmodule-compiler-option.md).  
  
 Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](./keycontainer-compiler-option.md). Použijte [-delaysign](./delaysign-compiler-option.md) , pokud chcete použít částečně podepsané sestavení.  
  
 V případě, že jsou zadány oba parametry-keyfile a-in (buď parametrem příkazového řádku nebo vlastním atributem) ve stejné kompilaci, kompilátor nejprve vyhledá kontejner klíčů. Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů. Pokud kompilátor nenalezne kontejner klíčů, pokusí se soubor určený parametrem-keyfile. Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči budou nainstalovány do kontejneru klíčů (podobně jako sn-i), takže při další kompilaci bude kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [Zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **podepisování** .  
  
3. Upravte vlastnost **soubor klíče se silným názvem** .  
  
 Pomocí <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>programu můžete programově získat přístup k této možnosti kompilátoru.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
