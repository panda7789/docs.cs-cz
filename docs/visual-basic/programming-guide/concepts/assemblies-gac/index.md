---
title: Sestavení a globální mezipaměti sestavení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Sestavení a globální mezipaměti sestavení (Visual Basic)
Tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení pro sestavení. Aplikace založené na síť. Sestavení podobu spustitelný soubor (.exe) nebo soubor dynamické knihovny (.dll) a jsou stavební kameny nástroje rozhraní .NET Framework. Modul common language runtime poskytují informace, musí se jednat o seznámen typu implementace. Si můžete představit jako kolekce typů a prostředků, které tvoří logickou jednotku funkčnosti a jsou sestaveny vzájemnou spolupráci sestavení.  
  
 Sestavení může obsahovat jeden nebo více modulů. Větší projekty mohou například plánujeme přidat tak, že několik jednotliví vývojáři pracovat na samostatných modulů, všechny nadcházející dohromady a vytvoří jednoho sestavení. Další informace o modulech, naleznete v tématu [jak: Vytváření vícesouborového sestavení](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Sestavení mají následující vlastnosti:  
  
-   Sestavení se implementují jako soubory .exe nebo .dll.  
  
-   Můžete sdílet sestavení mezi aplikacemi tak, že ji vložíte do globální mezipaměti sestavení. Sestavení musí být silným názvem předtím, než mohou být součástí globální mezipaměti sestavení. Další informace najdete v tématu [sestavení se silným názvem](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Sestavení jsou načtena do paměti pouze pokud jsou požadována. Pokud nejsou použity, nejsou načtené. To znamená, že sestavení mohou být účinný způsob, jak spravovat prostředky ve větších projektů.  
  
-   Informace o sestavení můžete získat prostřednictvím kódu programu pomocí reflexe. Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Pokud chcete načíst sestavení pouze chcete zkontrolovat, použijte metodu jako <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest sestavení  
 V rámci každé sestavení je *manifestu sestavení*. Podobně jako obsah, manifest sestavení obsahuje následující:  
  
-   Identita sestavení (jeho název a verzi).  
  
-   Soubor tabulku popisující všechny další soubory, které tvoří sestavení, například jiná sestavení, který jste vytvořili, že váš soubor .exe nebo .dll se může spolehnout, nebo dokonce rastrový obrázek nebo soubory Readme.  
  
-   *Seznam odkazů sestavení*, což je seznam všech externích závislostí – knihovny DLL debuggle nebo jiné soubory potřeby vaší aplikace, které byla pravděpodobně vytvořena jiným uživatelem. Odkazy na sestavení obsahují odkazy na globální i soukromá objekty. Globální objekty jsou umístěny v globální mezipaměti sestavení, oblast k dispozici pro jiné aplikace, o něco jako adresáři System32. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Obor názvů je příkladem sestavení v globální mezipaměti sestavení. Soukromé objekty musí být v adresáři na buď stejné úrovni jako nebo adresáři, ve kterém je nainstalována aplikace.  
  
 Protože sestavení obsahují informace o obsahu, správy verzí a závislostech, nespoléhejte na hodnoty registru Windows pro fungování aplikací, které vytvoříte pomocí jazyka Visual Basic. Sestavení omezit konflikty DLL a spolehlivější a usnadňuje nasazení, aby byly vaše aplikace. V mnoha případech můžete nainstalovat. Aplikace založené na NET jednoduše tak, že kopírováním jeho souborů k cílovému počítači.  
  
 Další informace najdete v části [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Přidání odkazu na sestavení  
 Pokud chcete použít sestavení, musíte přidat odkaz na ni. Dále použijete [Imports – příkaz](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) zvolte obor názvů položek, které chcete použít. Po sestavení odkazuje a importovat, všechny dostupné třídy, vlastnosti, metody a ostatní členy jeho obory názvů jsou k dispozici pro vaši aplikaci jako kdyby byly jejich kód částí zdrojového souboru.  
  
## <a name="creating-an-assembly"></a>Vytváření sestavení  
 Zkompilujte aplikaci sestavením z příkazového řádku pomocí kompilátoru příkazového řádku. Podrobnosti o vytváření sestavení z příkazového řádku najdete v tématu [sestavení z příkazového řádku](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  K vytvoření sestavení v sadě Visual Studio na **sestavení** nabídku zvolte **sestavení**.  
  
## <a name="see-also"></a>Viz také:
- [Sestavení v modulu CLR (Common Language Runtime)](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Přátelská sestavení (Visual Basic)](friend-assemblies.md)
- [Postupy: Sdílení sestavení s jinými aplikacemi (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)
- [Postupy: Zavedení a uvolnění sestavení (Visual Basic)](how-to-load-and-unload-assemblies.md)
- [Postupy: Určení, zda je soubor sestavení (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)
- [Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
