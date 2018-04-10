---
title: Sestavení a globální mezipaměti sestavení (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 893d869b1abaf9caa6f4705f40750912081d7df2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Sestavení a globální mezipaměti sestavení (Visual Basic)
Vytváří základní jednotku nasazení, Správa verzí, opakované použití, aktivaci oborů a oprávnění zabezpečení pro sestavení. Aplikace založené na Asp.net. Sestavení mít formu na spustitelný soubor (.exe) nebo soubor dynamické knihovny (DLL) a představují stavební kameny rozhraní .NET Framework. Poskytují modul common language runtime s použitím informací, musí se jednat o zjištění typu implementace. Si můžete představit jako kolekci typů a prostředky, které tvoří logickou jednotku funkcí a jsou vytvořeny tak spolupracují sestavení.  
  
 Sestavení může obsahovat jeden nebo více modulů. Například může být plánované větší projekty tak, že několik jednotlivých vývojáři fungovat na samostatné moduly, všechny příchozí dohromady a vytvoří jednoho sestavení. Další informace o modulech, naleznete v tématu [postupy: sestavení sestavení Multifile](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Sestavení mít následující vlastnosti:  
  
-   Sestavení se implementují jako soubory .exe nebo .dll.  
  
-   Můžete sdílet sestavení mezi aplikacemi umístěním v globální mezipaměti sestavení. Sestavení musí být silným názvem dříve než může být zahrnuta v globální mezipaměti sestavení. Další informace najdete v tématu [sestavení se silným názvem](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Sestavení jsou načtena do paměti, pouze pokud jsou požadována. Pokud se nepoužívají, nejsou načíst. To znamená, že sestavení může být účinný způsob, jak spravovat prostředky v větší projekty.  
  
-   Prostřednictvím kódu programu můžete získat informace o sestavení pomocí reflexe. Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Pokud chcete načíst sestavení pouze pro zkontrolovat, použijte metodu, jako <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest sestavení  
 V rámci každé sestavení je *manifest sestavení*. Podobně jako u obsahu, manifest sestavení obsahuje následující:  
  
-   Identity sestavení (její název a verzi).  
  
-   Soubor tabulku popisující všechna další soubory, které tvoří sestavení, například ostatních sestavení, které jste vytvořili, že váš soubor .exe nebo .dll spoléhá na, nebo i rastrového obrázku nebo souborech Readme.  
  
-   *Referenční seznam sestavení*, což je seznam všechny externí závislosti – knihoven DLL nebo jiné soubory potřebám vaší aplikace, které pravděpodobně byla vytvořena jiným uživatelem. Odkazy na sestavení obsahovat odkazy na globální a privátní objekty. Globální objekty jsou umístěny v globální mezipaměti sestavení, k dispozici pro jiné aplikace, poněkud jako adresáři System32 oblast. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Obor názvů je příkladem sestavení v globální mezipaměti sestavení. Privátní objekty musí být v adresáři na buď stejné úrovni jako nebo adresáři, ve kterém je nainstalována aplikace.  
  
 Protože sestavení obsahuje informace o obsahu, verze a závislosti, nespoléhejte na hodnoty registru systému Windows pro správné fungování aplikace, které vytvoříte v jazyce Visual Basic. Sestavení snižte .dll konflikty a spolehlivější a snazší nasazování zpřístupnit vaše aplikace. V mnoha případech můžete nainstalovat. Aplikace založené na NET jednoduše tak, že kopírování jeho soubory do cílového počítače.  
  
 Další informace najdete v části [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Přidat odkaz na sestavení  
 Pokud chcete použít sestavení, musíte přidat odkaz na jeho. V dalším kroku použijete [Imports – příkaz](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) vybrat obor názvů položky, které chcete použít. Po sestavení odkazuje a importovat, všechny dostupné třídy, vlastnosti, metod a ostatním členům jeho obory názvů jsou k dispozici do vaší aplikace jako svůj kód byly součástí zdrojového souboru.  
  
## <a name="creating-an-assembly"></a>Vytváření sestavení  
 Sestavování z příkazového řádku pomocí příkazového řádku kompilátoru kompilaci vaší aplikace. Podrobnosti o vytváření sestavení z příkazového řádku najdete v tématu [sestavení z příkazového řádku](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  K vytvoření sestavení v sadě Visual Studio na **sestavení** nabídce zvolte **sestavení**.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Přátelská sestavení (Visual Basic)](friend-assemblies.md)  
 [Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)  
 [Postupy: zavedení a uvolnění sestavení (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [Postupy: určení, zda je soubor sestavení (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)  
 [Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
