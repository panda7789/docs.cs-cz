---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: dd5e5612de15a499c0dce34dc30faa6fd5731c17
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124530"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Vývoj pro různé platformy pomocí přenosné knihovny tříd

Typ projektu přenositelné knihovny tříd v aplikaci Visual Studio vám pomůže rychle a snadno vytvářet aplikace a knihovny pro více platforem pro platformy Microsoft.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Přenositelné knihovny tříd vám můžou snížit čas a náklady na vývoj a testování kódu. Tento typ projektu použijte k zápisu a sestavení přenosných .NET Framework sestavení a pak na tato sestavení odkazovat z aplikací, které cílí na více platforem, jako je .NET Framework, iOS nebo Mac.

I po vytvoření přenositelného projektu knihovny tříd v aplikaci Visual Studio a zahájení jeho vývoje můžete změnit cílové platformy. Visual Studio zkompiluje vaši knihovnu s novými sestaveními, což vám pomůže identifikovat změny, které je třeba provést ve svém kódu.

## <a name="create-a-portable-class-library-project"></a>Vytvořit projekt přenositelné knihovny tříd

Chcete-li vytvořit přenosnou knihovnu tříd, použijte šablonu poskytnutou v aplikaci Visual Studio. Vytvořte nový projekt (**soubor** > **Nový projekt**) a v dialogovém okně **Nový projekt** vyberte programovací jazyk (vizuál C# nebo Visual Basic). Pak vyberte šablonu **Knihovna tříd (starší přenosná verze)** . Zadejte název projektu a klikněte na **tlačítko OK**.

Zobrazí se dialogové okno **Přidat přenosnou knihovnu tříd** . Zvolte dva nebo více cílů a pak zvolte **OK**.

![Přidání cílů přenosných knihoven tříd v aplikaci Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Změnit cíle

Cílové platformy projektu přenositelné knihovny tříd můžete změnit při jeho vytváření nebo po zahájení vývoje. Chcete-li změnit cíle po vytvoření projektu, v **Průzkumník řešení**otevřete místní nabídku pro váš projekt přenositelné knihovny tříd (nikoli řešení) a pak zvolte možnost **vlastnosti**. Na stránce Vlastnosti projektu se na kartě **Knihovna** zobrazují platformy, na které váš projekt aktuálně cílí.

![Vlastnosti projektu pro přenosnou knihovnu tříd v aplikaci Visual Studio](media/pcl-project-properties.png)

Chcete-li přidat nebo odebrat cíle, klikněte na tlačítko **změnit** a zaškrtněte políčka a zrušte zaškrtnutí příslušných políček.

Když změníte cíle, rozhraní API, která jsou k dispozici pro vývoj projektu, se změní tak, aby odpovídala vašemu výběru. Visual Studio hlásí chyby a upozornění, která se mohou vyskytnout v důsledku změny cílů.

Pokud chcete vyhodnotit přenositelnost vašich sestavení před provedením změn v aplikaci Visual Studio, můžete použít [analyzátor přenositelnosti .NET](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).

## <a name="supported-types-and-members"></a>Podporované typy a členy

Typy a členy, které jsou k dispozici v projektech přenositelné knihovny tříd, jsou omezeny několika faktory kompatibility:

- Musí být sdíleny napříč vybranými cíli.

- Se musí chovat podobně jako u těchto cílů.

- Nesmí se jednat o kandidáty na vyřazení.

- Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.

Pokud je člen podporovaný v knihovně přenosných tříd a pro vybrané cíle, zobrazí se ve vašem projektu v IntelliSense. Nezapomeňte však, že rozhraní API může být podporováno v přenositelné knihovně tříd, ale zda lze použít rozhraní API závisí na cílích, které vyberete.

## <a name="api-differences-in-the-portable-class-library"></a>Rozdíly v rozhraní API v přenosných knihovnách tříd

Chcete-li vytvořit přenosná sestavení knihovny tříd kompatibilní napříč všemi podporovanými platformami, některé členy byly v přenositelné knihovně tříd mírně změněny.

## <a name="use-the-portable-class-library"></a>Použití přenositelné knihovny tříd

Po sestavení přenositelného projektu knihovny tříd se na něj pouze odkazuje z jiných projektů. Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.

Chcete-li spustit aplikaci, která odkazuje na přenositelné sestavení knihovny tříd, musí být v počítači nainstalována požadovaná verze (nebo novější) cílových platforem. Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci spustit bez dalších úprav na počítači, který jste použili k vývoji aplikace.

### <a name="deploy-a-universal-windows-app"></a>Nasazení univerzální aplikace pro Windows

Při vytváření univerzální aplikace pro Windows, která odkazuje na přenositelné sestavení knihovny tříd, je vše, co potřebujete k nasazení aplikace, součástí balíčku aplikace a nejsou potřeba žádné další kroky.

### <a name="deploy-a-net-framework-app"></a>Nasazení aplikace .NET Framework

Když nasadíte aplikaci .NET Framework, která odkazuje na přenositelné sestavení knihovny tříd, je nutné zadat závislost na správné verzi .NET Framework. Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.

- Vytvoření závislosti s nasazením ClickOnce: v **Průzkumník řešení**vyberte uzel projektu pro projekt, který chcete publikovat. (Jedná se o projekt, který odkazuje na přenosný projekt knihovny tříd.) Na panelu nabídek zvolte **vlastnosti** **projektu** > a pak klikněte na kartu **publikovat** . Na stránce **publikovat** vyberte **požadované součásti**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

- Vytvoření závislosti pomocí projektu instalace: v **Průzkumník řešení**vyberte projekt instalace. Na panelu nabídek vyberte **vlastnosti** **projektu** >  > **předpoklady**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

Další informace o nasazení aplikací .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Viz také

- [Používání knihovny přenosných tříd spolu s modelem MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [Prostředky aplikací pro knihovny cílené na více platforem](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analyzátor přenositelnosti .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Nasazení](../../../docs/framework/deployment/net-framework-applications.md)
