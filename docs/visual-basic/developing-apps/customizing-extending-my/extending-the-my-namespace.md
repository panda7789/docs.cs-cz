---
title: Rozšíření oboru názvů My v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 4d7bb6eef398746a4bd2dc4dbf3d526da1c1e0f1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814148"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozšíření oboru názvů My v jazyce Visual Basic
`My` Oboru názvů v jazyce Visual Basic zveřejňuje vlastnosti a metody, které vám umožní snadno využít sílu rozhraní .NET Framework. `My` Obor názvů zjednodušuje běžné programovací problémy, často zkracuje těžký úkol jediný řádek kódu. Kromě toho `My` obor názvů je plně rozšiřitelná tak, aby si můžete přizpůsobit chování `My` a přidávat nové služby do své hierarchie umožní reagovat na potřeby konkrétní aplikace. Toto téma popisuje, jak tom, jak přizpůsobit stávající členové `My` obor názvů a přidání své vlastní třídy pro `My` oboru názvů.  
  
 **Obsah témat**  
  
-   [Přizpůsobení stávajících členů My Namespace](#customizing)  
  
-   [Přidávání členů do Moje objekty](#addingtoobjects)  
  
-   [Přidání vlastních objektů do My Namespace](#addingcustom)  
  
-   [Přidání členů My Namespace](#addingtonamespace)  
  
-   [Přidání události do vlastní objekty](#addingevents)  
  
-   [Pokyny k návrhu](#design)  
  
-   [Navrhování knihoven tříd pro Moje](#designing)  
  
-   [Zabalení a nasazení rozšíření](#packaging)  
  
## <a name="customizing"></a> Přizpůsobení stávajících členů My Namespace  
 `My` Oboru názvů ve Visual Basic zpřístupňuje často používané informace o vaší aplikace, počítače a další. Úplný seznam objektů v `My` obor názvů, naleznete v tématu [My Reference](../../../visual-basic/language-reference/keywords/my-reference.md). Možná budete muset upravit stávající členové `My` oboru názvů tak, aby lépe odpovídaly potřebám vaší aplikace. Nějaká vlastnost v objektu `My` obor názvů, který není jen pro čtení můžete nastavit vlastní hodnoty.  
  
 Předpokládejme například, že často používáte `My.User` objektu pro přístup k aktuální kontext zabezpečení pro uživatele s vaší aplikací. Však vaše společnost používá vlastní uživatelské objekt ke zveřejnění dalších informací a možnosti pro uživatele v rámci společnosti. V tomto scénáři můžete nahradit výchozí hodnota `My.User.CurrentPrincipal` vlastnost s instance vašeho vlastního objektu zabezpečení objektu, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]  
  
 Nastavení `CurrentPrincipal` vlastnost `My.User` objekt změní identitu, pod kterým je aplikace spuštěná. `My.User` Objektu, pak vrátí informace o nově zadaný uživatel.  
  
## <a name="addingtoobjects"></a> Přidávání členů do Moje objekty  
 Typy vrácených `My.Application` a `My.Computer` jsou definované jako `Partial` třídy. Proto můžete rozšířit `My.Application` a `My.Computer` objekty tak, že vytvoříte `Partial` třídu s názvem `MyApplication` nebo `MyComputer`. Třída nemůže být `Private` třídy. Pokud zadáte třídy jako součást `My` obor názvů, můžete přidat vlastnosti a metody, které budou součástí `My.Application` nebo `My.Computer` objekty.  
  
 Například následující příklad přidá vlastnost s názvem `DnsServerIPAddresses` k `My.Computer` objektu.  
  
 [!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]  
  
## <a name="addingcustom"></a> Přidání vlastních objektů do My Namespace  
 I když `My` obor názvů poskytuje řešení pro spoustu běžných programovacích úkolů, můžete narazit na úlohy, které `My` adresy oboru názvů. Například aplikace může přístup ke službám vlastní adresáře pro data uživatelů, nebo vaše aplikace může používat sestavení, které nejsou nainstalované ve výchozím nastavení s jazykem Visual Basic. Můžete rozšířit `My` obor názvů pro zahrnutí vlastních řešení pro běžné úlohy, které jsou specifické pro vaše prostředí. `My` Oboru názvů lze snadno rozšířit o nové členy pro rostoucí potřeby aplikací. Kromě toho můžete nasadit váš `My` rozšíření oboru názvů s ostatními vývojáři jako šablony jazyka Visual Basic.  
  
### <a name="addingtonamespace"></a> Přidání členů My Namespace  
 Protože `My` je obor názvů jako jiný obor názvů, můžete přidat vlastnosti nejvyšší úrovně do něj pouze přidáním modulu a určením `Namespace` z `My`. Modul s poznámkami `HideModuleName` atributu, jak je znázorněno v následujícím příkladu. `HideModuleName` Atribut zajišťuje, aby IntelliSense nebudou zobrazovat název modulu zobrazí členy `My` oboru názvů.  
  
 [!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]  
  
 Přidávat členy do `My` obor názvů, přidejte vlastnosti podle potřeby do modulu. Pro každou vlastnost přidá do `My` obor názvů, přidejte privátní pole typu `ThreadSafeObjectProvider(Of T)`, kde typ je typ vrácený vlastní vlastnosti. Toto pole se používá k vytvoření instance objektu bezpečným pro vlákno má být vrácen ve vlastnosti voláním `GetInstance` metody. V důsledku toho každý podproces, který přistupuje k rozšířené vlastnosti obdrží svoji vlastní instanci vrácený typ. Následující příklad přidá vlastnost s názvem `SampleExtension` , který je typu `SampleExtension` k `My` obor názvů:  
  
 [!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]  
  
## <a name="addingevents"></a> Přidání události do vlastní objekty  
 Můžete použít `My.Application` objektu k vystavení události pro vaše vlastní `My` objektů tím, že rozšíří `MyApplication` částečné třídy v `My` oboru názvů. Pro projekty založené na Windows, můžete dvakrát kliknout **Můj projekt** uzlu v projektu v **Průzkumníka řešení**. V jazyce Visual Basic **Návrháře projektu**, klikněte na tlačítko `Application` kartu a potom klikněte na tlačítko `View Application Events` tlačítko. Vytvoří se nový soubor, který je pojmenován ApplicationEvents.vb. Obsahuje následující kód pro rozšíření `MyApplication` třídy.  
  
 [!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]  
  
 Přidáte obslužné rutiny událostí pro své vlastní `My` objekty tak, že přidáte vlastní obslužné rutiny pro `MyApplication` třídy. Vlastní události vám umožňují přidat kód, který se spustí při přidání obslužné rutiny události odebrán, nebo se vyvolá událost. Všimněte si, `AddHandler` kód pro vlastní událost se spustí jenom v případě, že kód je přidal uživatel, který chcete zpracovat událost. Představte si třeba, který `SampleExtension` má objekt z předchozí části `Load` události, ke které chcete přidat vlastní obslužnou rutinu události pro. Následující příklad kódu ukazuje vlastní obslužnou rutinu s názvem `SampleExtensionLoad` , která bude vyvolána v případě `My.SampleExtension.Load` dojde k události. Při přidání kódu pro zpracování nové `My.SampleExtensionLoad` události, `AddHandler` je proveden součástí tohoto kódu vlastní události. `MyApplication_SampleExtensionLoad` Metoda je součástí ukázky kódu slouží jako ukázka obslužnou rutinu události, která zpracovává `My.SampleExtensionLoad` událostí. Všimněte si, že `SampleExtensionLoad` událostí bude k dispozici, když vyberete **Moje aplikace události** možnost v levém rozevíracího seznamu výše editoru kódu při úpravách souboru ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]  
  
## <a name="design"></a> Pokyny k návrhu  
 Při vývoji rozšíření pro `My` obor názvů, použijte následující pokyny a tím pomáhá minimalizovat náklady na údržbu součástí rozšíření.  
  
-   **Zahrnout pouze logiku rozšíření.** Součástí logiky `My` rozšíření oboru názvů by měl obsahovat pouze kód, který je potřeba k požadované funkci v `My` oboru názvů. Vzhledem k tomu, že vaše rozšíření se bude nacházet v projektech uživatele jako zdrojový kód, aktualizuje se rozšíření komponenty způsobuje vysoké náklady na údržbu a mělo by se vyhnout Pokud je to možné.  
  
-   **Minimalizujte předpoklady projekt.** Při vytváření vašeho rozšíření `My` obor názvů, Nepředpokládejte sada odkazů, importů na úrovni projektu nebo specifické nastavení kompilátoru (například `Option Strict` vypnuto). Místo toho minimalizovaly závislosti a plně kvalifikovat pomocí odkazů na všechny typy `Global` – klíčové slovo. Také se ujistěte, že rozšíření kompiluje s `Option Strict` on, chcete-li minimalizovat chyby v rozšíření.  
  
-   **Izolace kódu rozšíření.** Umístění kódu do jednoho souboru díky rozšíření jednoduše nasadit jako šablonu položky sady Visual Studio. Další informace najdete v tématu "Balení a nasazení rozšíření" dále v tomto tématu. Umístění všech `My` kódu rozšíření oboru názvů do jednoho souboru nebo do samostatné složky v projektu vám také pomůže uživatelům najít `My` rozšíření oboru názvů.  
  
## <a name="designing"></a> Navrhování knihoven tříd pro Moje  
 Jak je tomu u většiny objektové modely, některé vzory návrhu dobře fungovaly v `My` obor názvů a jiné nikoli. Při navrhování rozšíření `My` obor názvů, zvažte následující zásady:  
  
-   **Bezstavové metody.** Metody v `My` oboru názvů by měla poskytnout kompletní řešení ke konkrétnímu úkolu. Ujistěte se, že hodnoty parametrů, které jsou předány do metody poskytují všechny vstupy potřeba provést určitý úkol. Vyhněte se vytváření metody, které spoléhají na předchozí stav, jako je otevření připojení k prostředkům.  
  
-   **Globální instance.** Jenom stav, který se spravuje v `My` obor názvů je globální do projektu. Například `My.Application.Info` zapouzdří stav, který se sdílí v celé aplikaci.  
  
-   **Jednoduché typy parametrů.** Zjednodušení složitých typů parametrů se vyhnout. Místo toho vytvořit metody, které buď žádný vstupní parametr přijímají nebo, která přijímá jednoduchý vstupní typy, jako jsou řetězce, primitivní typy a tak dále.  
  
-   **Metody pro vytváření objektů.** Některé typy je obtížné vytvořit instanci. Poskytuje metody pro vytváření objektů jako rozšíření `My` obor názvů umožňuje snadno objevit a používat typy, které do této kategorie patří. Je například metoda factory, která funguje dobře `My.Computer.FileSystem.OpenTextFileReader`. Existuje několik typů datového proudu k dispozici v rozhraní .NET Framework. Konkrétně zadáním textové soubory `OpenTextFileReader` pomáhá uživatelům pochopit, které datový proud použít.  
  
 Tyto pokyny nebrání Principy návrhu obecné pro knihovny tříd. Namísto toho jsou doporučení, která jsou optimalizovaná pro vývojáře, kteří používají Visual Basic a `My` oboru názvů. Principy návrhu obecné pro vytvoření knihovny tříd, naleznete v tématu [pokyny k návrhu architektury](../../../standard/design-guidelines/index.md).  
  
## <a name="packaging"></a> Zabalení a nasazení rozšíření  
 Můžete zahrnout `My` rozšíření oboru názvů v šabloně projektu sady Visual Studio, nebo můžete balíček rozšíření a nasazovat je jako šablonu položky sady Visual Studio. Když vytvoříte balíček vaše `My` rozšíření oboru názvů jako šablonu položky sady Visual Studio, můžete využít výhod další funkce poskytované jazyka Visual Basic. Tyto možnosti umožňují zahrnout rozšíření, když projekt odkazuje na konkrétní sestavení nebo povolit uživatelům explicitně přidat váš `My` rozšíření oboru názvů pomocí **Moje rozšíření** stránky jazyka Visual Basic Návrhář projektu.  
  
 Podrobnosti o tom, jak nasadit `My` rozšíření oboru názvů, naleznete v tématu [balení a nasazení Moje rozšíření pro vlastní](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Viz také:

- [Balení a nasazení vlastních rozšíření oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
