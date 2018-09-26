---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172703"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Vývoj pro různé platformy pomocí přenosné knihovny tříd

Typ knihovny přenosných tříd projektu v sadě Visual Studio pomáhá rychle a snadno vytvářet aplikace pro různé platformy a knihovny pro platformy Microsoft.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Přenosné knihovny tříd můžete zkrátit čas a náklady na vývoj a testování kódu. Použít tento typ projektu můžete zapisovat a sestavovat přenosná sestavení rozhraní .NET Framework a odkázat na tato sestavení z aplikace, které se vyvíjet pro víc platforem, jako je například rozhraní .NET Framework, iOS nebo Mac

I po vytvoření projektu přenosné knihovny tříd v sadě Visual Studio a začít s vývojem ho můžete změnit cílové platformy. Visual Studio zkompiluje knihovny pomocí nové sestavení, který vám pomůže identifikovat změny, které je třeba provést v kódu.

## <a name="create-a-portable-class-library-project"></a>Vytvoření projektu knihovny přenosných tříd

K vytvoření přenosné knihovny tříd pomocí šablony v sadě Visual Studio k dispozici. Vytvoření nového projektu (**souboru** > **nový projekt**) a **nový projekt** dialogového okna, vyberte svůj oblíbený programovací jazyk (Visual C# nebo Visual Basic). Vyberte **knihovna tříd (starší přenosná)** šablony. Zadejte název pro váš projekt a zvolte **OK**.

**Přidat přenosnou knihovnu tříd** zobrazí se dialogové okno. Vyberte dvě nebo více cílů a klikněte na tlačítko **OK**.

![Přidání cíle představující knihovny přenosných tříd v sadě Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Změnit cíle

Při vytváření nebo poté, co jste začali vývoje můžete změnit cílové platformy projektu knihovny přenosných tříd. Pokud chcete změnit cíle po vytvoření projektu v **Průzkumníka řešení**, otevřete místní nabídku projektu přenosné knihovny tříd (nikoli řešení) a klikněte na tlačítko **vlastnosti** . Na stránce Vlastnosti projektu **knihovny** karta zobrazuje platformy, že aktuálně váš projekt cílí.

![Vlastnosti projektu pro přenosné knihovny tříd v sadě Visual Studio](media/pcl-project-properties.png)

Chcete-li přidat nebo odebrat cíle, zvolte **změnu** tlačítko a potom vyberte a zrušte zaškrtnutí příslušných políček.

Při změně cíle, které rozhraní API, která jsou k dispozici pro vývoj projektu se změní podle vašeho výběru. Visual Studio hlásí chyby a upozornění, které mohou nastat v důsledku změny cíle.

Pokud chcete vyhodnotit přenositelnost vašeho sestavení před provádět změny v sadě Visual Studio, můžete použít [.NET Portability Analyzeru](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).

## <a name="supported-types-and-members"></a>Podporované typy a členy

Typy a členy, které jsou k dispozici v projektech knihovny přenosných tříd jsou omezeny několika faktory kompatibility:

-   Musí být sdíleny napříč cíli, který jste vybrali.

-   Musí chovat podobně napříč těmito cíli.

-   Nesmí se jednat o kandidáty na vyřazení.

-   Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.

Pokud člen je podporován v přenosné knihovny tříd a pro vybrané cíle, zobrazí se v projektu v technologii IntelliSense. Nezapomeňte však, že rozhraní API může nepodporuje v přenosné knihovně tříd, ale, zda můžete použít rozhraní API závisí na cíle, které můžete vybrat.

## <a name="api-differences-in-the-portable-class-library"></a>API – rozdíly v přenosné knihovně tříd

Chcete-li sestavení knihovny přenosných tříd kompatibilní na všech podporovaných platformách, změna některých členů se poněkud in Portable Class Library.

## <a name="use-the-portable-class-library"></a>Použití přenosné knihovny tříd

Po vytvoření projektu knihovny přenosných tříd něj můžete odkazovat z jiných projektů. Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.

Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, požadovaná verze (nebo novější) verze cílových platforem musí být nainstalován v počítači. Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci bez další úpravy spustit na počítači, který jste použili při vývoji aplikace.

### <a name="deploy-a-universal-windows-app"></a>Nasazení aplikace pro Universal Windows

Při vytváření aplikace Universal Windows, která odkazuje na sestavení knihovny přenosných tříd, všechno, co potřebujete k nasazení aplikace je součástí balíčku aplikace a nejsou vyžadovány žádné další kroky.

### <a name="deploy-a-net-framework-app"></a>Nasazení .NET Framework aplikace

Když nasadíte aplikaci .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, je nutné určit závislost na správnou verzi rozhraní .NET Framework. Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.

-   Vytvoření závislosti s nasazením ClickOnce: V **Průzkumníka řešení**, zvolte uzel projektu pro projekt, kterou chcete publikovat. (Jedná se o projekt, který odkazuje na projekt knihovny přenosných tříd.) V panelu nabídky zvolte **projektu** > **vlastnosti**a klikněte na tlačítko **publikovat** kartu. Na **publikovat** zvolte **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

-   Vytvoření závislosti pomocí projektu instalace: V **Průzkumníka řešení**, vyberte projekt instalace. V panelu nabídky zvolte **projektu** > **vlastnosti** > **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.

Další informace o nasazení aplikací rozhraní .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Viz také:

- [Používání knihovny přenosných tříd spolu s modelem MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [Prostředky aplikací pro knihovny cílené na více platforem](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET portability Analyzeru](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Nasazení](../../../docs/framework/deployment/net-framework-applications.md)
