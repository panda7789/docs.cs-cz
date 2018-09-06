---
title: Sestavení a globální mezipaměti sestavení (C#)
ms.date: 07/20/2015
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: ed5ecff57035b4d3cf47f8325fe5c172180f9d40
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042293"
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Sestavení a globální mezipaměti sestavení (C#)
Tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení pro sestavení. Aplikace založené na síť. Sestavení podobu spustitelný soubor (.exe) nebo soubor dynamické knihovny (.dll) a jsou stavební kameny nástroje rozhraní .NET Framework. Modul common language runtime poskytují informace, musí se jednat o seznámen typu implementace. Si můžete představit jako kolekce typů a prostředků, které tvoří logickou jednotku funkčnosti a jsou sestaveny vzájemnou spolupráci sestavení.  
  
 Sestavení může obsahovat jeden nebo více modulů. Větší projekty mohou například plánujeme přidat tak, že několik jednotliví vývojáři pracovat na samostatných modulů, všechny nadcházející dohromady a vytvoří jednoho sestavení. Další informace o modulech, naleznete v tématu [postupy: vytváření sestavení Multifile](../../../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Sestavení mají následující vlastnosti:  
  
-   Sestavení se implementují jako soubory .exe nebo .dll.  
  
-   Můžete sdílet sestavení mezi aplikacemi tak, že ji vložíte do globální mezipaměti sestavení. Sestavení musí být silným názvem předtím, než mohou být součástí globální mezipaměti sestavení. Další informace najdete v tématu [sestavení se silným názvem](../../../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Sestavení jsou načtena do paměti pouze pokud jsou požadována. Pokud nejsou použity, nejsou načtené. To znamená, že sestavení mohou být účinný způsob, jak spravovat prostředky ve větších projektů.  
  
-   Informace o sestavení můžete získat prostřednictvím kódu programu pomocí reflexe. Další informace najdete v tématu [reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Pokud chcete načíst sestavení pouze chcete zkontrolovat, použijte metodu jako <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest sestavení  
 V rámci každé sestavení, je *manifestu sestavení*. Podobně jako obsah, manifest sestavení obsahuje následující:  
  
-   Identita sestavení (jeho název a verzi).  
  
-   Soubor tabulku popisující všechny další soubory, které tvoří sestavení, například jiná sestavení, který jste vytvořili, že váš soubor .exe nebo .dll se může spolehnout, nebo dokonce rastrový obrázek nebo soubory Readme.  
  
-   *Seznam odkazů sestavení*, což je seznam všech externích závislostí – knihovny DLL debuggle nebo jiné soubory potřeby vaší aplikace, které byla pravděpodobně vytvořena jiným uživatelem. Odkazy na sestavení obsahují odkazy na globální i soukromá objekty. Globální objekty jsou umístěny v globální mezipaměti sestavení, oblast k dispozici pro jiné aplikace. Soukromé objekty musí být v adresáři na buď stejné úrovni jako nebo adresáři, ve kterém je nainstalována aplikace.  
  
 Protože sestavení obsahují informace o obsahu, správy verzí a závislostech, nespoléhejte na hodnoty registru Windows pro fungování aplikací, které vytvoříte pomocí jazyka C#. Sestavení omezit konflikty DLL a spolehlivější a usnadňuje nasazení, aby byly vaše aplikace. V mnoha případech můžete nainstalovat. Aplikace založené na NET jednoduše tak, že kopírováním jeho souborů k cílovému počítači.  
  
 Další informace najdete v části [Manifest sestavení](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Přidání odkazu na sestavení  
 Pokud chcete použít sestavení, musíte přidat odkaz na ni. Dále použijete [direktiva using](../../../../csharp/language-reference/keywords/using-directive.md) zvolte obor názvů položek, které chcete použít. Po sestavení odkazuje a importovat, všechny dostupné třídy, vlastnosti, metody a ostatní členy jeho obory názvů jsou k dispozici pro vaši aplikaci jako kdyby byly jejich kód částí zdrojového souboru.  
  
 V jazyce C# můžete také použít dvě verze téhož sestavení se v jedné aplikaci. Další informace najdete v tématu [externí alias](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Vytváření sestavení  
 Zkompilujte aplikaci kliknutím **sestavení** na **sestavení** nabídky nebo vytvořením z příkazového řádku pomocí kompilátoru příkazového řádku. Podrobnosti o vytváření sestavení z příkazového řádku najdete v tématu [sestavení pomocí příkazového řádku csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  K vytvoření sestavení v sadě Visual Studio na **sestavení** nabídku zvolte **sestavení**.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Sestavení v modulu CLR (Common Language Runtime)](../../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Přátelská sestavení (C#)](friend-assemblies.md)  
- [Postupy: sdílení sestavení s jinými aplikacemi (C#)](how-to-share-an-assembly-with-other-applications.md)  
- [Postupy: zavedení a uvolnění sestavení (C#)](how-to-load-and-unload-assemblies.md)  
- [Postupy: určení, zda je soubor sestavení (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
- [Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
