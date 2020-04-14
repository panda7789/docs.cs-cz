---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242800"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Vývoj napříč platformami s knihovnou přenosných tříd

Typ projektu Knihovna přenosných tříd v sadě Visual Studio vám pomůže rychle a snadno vytvářet aplikace a knihovny pro různé platformy pro platformy Microsoftu.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Přenosné knihovny tříd vám mohou pomoci zkrátit čas a náklady na vývoj a testování kódu. Tento typ projektu slouží k zápisu a vytváření přenosných sestavení rozhraní .NET Framework a potom odkazovat na tato sestavení z aplikací, které cílí na více platforem, jako je rozhraní .NET Framework, iOS nebo Mac.

I po vytvoření projektu knihovny přenosných tříd v sadě Visual Studio a jeho zahájení jeho vývoje můžete změnit cílové platformy. Visual Studio zkompiluje vaši knihovnu s novými sestaveními, které vám pomohou identifikovat změny, které je třeba provést v kódu.

## <a name="create-a-portable-class-library-project"></a>Vytvoření projektu knihovny přenosných tříd

Chcete-li vytvořit knihovnu přenosných tříd, použijte šablonu poskytnutou v sadě Visual Studio. Vytvořte nový projekt **(Soubor** > **nový projekt**) a v dialogovém okně Nový **projekt** vyberte programovací jazyk (Visual C# nebo Visual Basic). Potom vyberte šablonu **Knihovna tříd (Starší přenosné).** Zadejte název projektu a zvolte **OK**.

Zobrazí se dialogové okno **Přidat knihovnu přenosných tříd.** Zvolte dva nebo více cílů a pak zvolte **OK**.

![Přidání cílů knihovny přenosných tříd v sadě Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Změnit cíle

Cílové platformy projektu knihovny přenosných tříd můžete změnit, když jej vytvoříte nebo po spuštění vývoje. Pokud chcete změnit cíle po vytvoření projektu, otevřete v **Průzkumníku řešení**místní nabídku pro projekt knihovny přenosných tříd (nikoli řešení) a pak zvolte **Vlastnosti**. Na stránce vlastností projektu karta **Knihovna** zobrazuje platformy, na které projekt aktuálně cílí.

![Vlastnosti projektu pro přenosnou knihovnu tříd v sadě Visual Studio](media/pcl-project-properties.png)

Chcete-li přidat nebo odebrat cíle, zvolte tlačítko **Změnit** a zaškrtněte a zrušte zaškrtnutí příslušných políček.

Změníte-li cíle, rozhraní API, která jsou k dispozici pro vývoj projektu, se změní tak, aby odpovídala vašemu výběru. Visual Studio hlásí chyby a upozornění, které mohou nastat v důsledku změny cílů.

Pokud chcete vyhodnotit přenositelnost sestavení před prováděním změn v sadě Visual Studio, můžete použít [nástroj .NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Podporované typy a členy

Typy a členy, které jsou k dispozici v projektech knihovny přenosných tříd, jsou omezeny několika faktory kompatibility:

- Musí být sdíleny mezi vybranými cíli.

- Musí se chovat podobně mezi těmito cíli.

- Nesmí se jednat o kandidáty na vyřazení.

- Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.

Pokud je člen podporován v knihovně přenosných tříd a pro vybrané cíle, zobrazí se v projektu v aplikaci IntelliSense. Nezapomeňte však, že rozhraní API může být podporováno v knihovně přenosných tříd, ale to, zda můžete rozhraní API použít, závisí na vybraných cílech.

## <a name="api-differences-in-the-portable-class-library"></a>Rozdíly rozhraní API v knihovně přenosných tříd

Aby byla sestavení knihovny přenosných tříd kompatibilní na všech podporovaných platformách, některé členy byly v knihovně přenosných tříd mírně změněny.

## <a name="use-the-portable-class-library"></a>Použití knihovny přenosných tříd

Po sestavení projektu knihovny přenosných tříd, stačí odkazovat z jiných projektů. Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.

Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, musí být v počítači nainstalována požadovaná verze (nebo novější) cílových platforem. Visual Studio obsahuje všechny požadované architektury, takže můžete spustit aplikaci bez dalších úprav v počítači, který jste použili k vývoji aplikace.

### <a name="deploy-a-universal-windows-app"></a>Nasazení univerzální aplikace pro Windows

Když vytvoříte univerzální aplikaci pro Windows, která odkazuje na sestavení knihovny přenosných tříd, vše, co potřebujete k nasazení aplikace, je zahrnuto v balíčku aplikace a nejsou vyžadovány žádné další kroky.

### <a name="deploy-a-net-framework-app"></a>Nasazení aplikace rozhraní .NET Framework

Při nasazení aplikace rozhraní .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, je nutné zadat závislost na správné verzi rozhraní .NET Framework. Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.

- Chcete-li vytvořit závislost pomocí funkce ClickOnce: V **Průzkumníku řešení**, zvolte uzel projektu pro projekt, který chcete publikovat. (Jedná se o projekt, který odkazuje na projekt knihovny přenosných tříd.) Na řádku nabídek zvolte**Vlastnosti** **projektu** > a pak zvolte kartu **Publikovat.** Na stránce **Publikovat** zvolte **Požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

- Chcete-li vytvořit závislost s projektem instalace: V **Průzkumníku řešení**zvolte projekt instalace. Na řádku nabídek zvolte**Požadavky****na vlastnosti** >  **projektu** > . Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

Další informace o nasazení aplikací rozhraní .NET Framework naleznete v [Příručce k nasazení pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Viz také

- [Používání knihovny přenosných tříd spolu s modelem MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Prostředky aplikací pro knihovny, které cílí na více platforem](app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analyzátor přenosové schopnosti rozhraní .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Nasazení](../../../docs/framework/deployment/net-framework-applications.md)
