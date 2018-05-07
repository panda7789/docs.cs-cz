---
title: Sestavení a globální mezipaměti sestavení (C#)
ms.date: 07/20/2015
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 994498525aed3ebb08f2de7926c7adc2d3d95f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Sestavení a globální mezipaměti sestavení (C#)
Vytváří základní jednotku nasazení, Správa verzí, opakované použití, aktivaci oborů a oprávnění zabezpečení pro sestavení. Aplikace založené na Asp.net. Sestavení mít formu na spustitelný soubor (.exe) nebo soubor dynamické knihovny (DLL) a představují stavební kameny rozhraní .NET Framework. Poskytují modul common language runtime s použitím informací, musí se jednat o zjištění typu implementace. Si můžete představit jako kolekci typů a prostředky, které tvoří logickou jednotku funkcí a jsou vytvořeny tak spolupracují sestavení.  
  
 Sestavení může obsahovat jeden nebo více modulů. Například může být plánované větší projekty tak, že několik jednotlivých vývojáři fungovat na samostatné moduly, všechny příchozí dohromady a vytvoří jednoho sestavení. Další informace o modulech, naleznete v tématu [postupy: sestavení sestavení Multifile](../../../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Sestavení mít následující vlastnosti:  
  
-   Sestavení se implementují jako soubory .exe nebo .dll.  
  
-   Můžete sdílet sestavení mezi aplikacemi umístěním v globální mezipaměti sestavení. Sestavení musí být silným názvem dříve než může být zahrnuta v globální mezipaměti sestavení. Další informace najdete v tématu [sestavení se silným názvem](../../../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Sestavení jsou načtena do paměti, pouze pokud jsou požadována. Pokud se nepoužívají, nejsou načíst. To znamená, že sestavení může být účinný způsob, jak spravovat prostředky v větší projekty.  
  
-   Prostřednictvím kódu programu můžete získat informace o sestavení pomocí reflexe. Další informace najdete v tématu [reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Pokud chcete načíst sestavení pouze pro zkontrolovat, použijte metodu, jako <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest sestavení  
 V rámci každé sestavení je *manifest sestavení*. Podobně jako u obsahu, manifest sestavení obsahuje následující:  
  
-   Identity sestavení (její název a verzi).  
  
-   Soubor tabulku popisující všechna další soubory, které tvoří sestavení, například ostatních sestavení, které jste vytvořili, že váš soubor .exe nebo .dll spoléhá na, nebo i rastrového obrázku nebo souborech Readme.  
  
-   *Referenční seznam sestavení*, což je seznam všechny externí závislosti – knihoven DLL nebo jiné soubory potřebám vaší aplikace, které pravděpodobně byla vytvořena jiným uživatelem. Odkazy na sestavení obsahovat odkazy na globální a privátní objekty. Globální objekty jsou umístěny v globální mezipaměti sestavení, oblast k dispozici pro jiné aplikace. Privátní objekty musí být v adresáři na buď stejné úrovni jako nebo adresáři, ve kterém je nainstalována aplikace.  
  
 Protože sestavení obsahuje informace o obsahu, verze a závislosti, nespoléhejte na hodnoty registru systému Windows pro správné fungování aplikace, které vytvoříte pomocí C#. Sestavení snižte .dll konflikty a spolehlivější a snazší nasazování zpřístupnit vaše aplikace. V mnoha případech můžete nainstalovat. Aplikace založené na NET jednoduše tak, že kopírování jeho soubory do cílového počítače.  
  
 Další informace najdete v části [Manifest sestavení](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Přidat odkaz na sestavení  
 Pokud chcete použít sestavení, musíte přidat odkaz na jeho. V dalším kroku použijete [using – direktiva](../../../../csharp/language-reference/keywords/using-directive.md) vybrat obor názvů položky, které chcete použít. Po sestavení odkazuje a importovat, všechny dostupné třídy, vlastnosti, metod a ostatním členům jeho obory názvů jsou k dispozici do vaší aplikace jako svůj kód byly součástí zdrojového souboru.  
  
 V jazyce C# můžete také použít dvě verze stejného sestavení v jedné aplikaci. Další informace najdete v tématu [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Vytváření sestavení  
 Zkompilujte aplikaci kliknutím **sestavení** na **sestavení** nabídky nebo sestavení z příkazového řádku pomocí příkazového řádku kompilátoru. Podrobnosti o vytváření sestavení z příkazového řádku najdete v tématu [vytváření pomocí příkazového řádku csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  K vytvoření sestavení v sadě Visual Studio na **sestavení** nabídce zvolte **sestavení**.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Přátelská sestavení (C#)](friend-assemblies.md)  
 [Postupy: sdílení sestavení s jinými aplikacemi (C#)](how-to-share-an-assembly-with-other-applications.md)  
 [Postupy: zavedení a uvolnění sestavení (C#)](how-to-load-and-unload-assemblies.md)  
 [Postupy: určení, zda je soubor sestavení (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
 [Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [Návod: Vložení typů z řízených sestavení v sadě Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
