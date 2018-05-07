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
ms.openlocfilehash: 22d9d0def302b870de6f3e5ca4c142758b21314c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozšíření oboru názvů My v jazyce Visual Basic
`My` Oboru názvů v jazyce Visual Basic zpřístupňuje vlastnosti a metody, které vám umožní snadno využití výkonu rozhraní .NET Framework. `My` Obor názvů zjednodušuje běžné programovací problémy, často zkracuje snadné jednořádkového kódu. Kromě toho `My` obor názvů je plná rozšiřitelnost tak, aby si můžete přizpůsobit chování `My` a přidání nových služeb do jeho hierarchie k přizpůsobení potřebám specifické aplikace. Toto téma popisuje, jak postup přizpůsobení stávající členy `My` obor názvů a jak přidat vlastní třídy k `My` oboru názvů.  
  
 **Obsah tématu**  
  
-   [Přizpůsobení existující My Namespace členy](#customizing)  
  
-   [Přidávání členů do mé objekty](#addingtoobjects)  
  
-   [Přidání vlastních objektů do My Namespace](#addingcustom)  
  
-   [Přidávání členů do My Namespace](#addingtonamespace)  
  
-   [Přidávání událostí do vlastní objekty](#addingevents)  
  
-   [Pokyny pro návrh](#design)  
  
-   [Navrhování knihovny tříd pro Moje](#designing)  
  
-   [Balení a nasazení rozšíření](#packaging)  
  
##  <a name="customizing"></a> Přizpůsobení existující My Namespace členy  
 `My` Oboru názvů v jazyce Visual Basic zpřístupňuje často používané informace o aplikaci, počítače a další. Úplný seznam objektů `My` obor názvů, najdete v části [Moje odkaz](../../../visual-basic/language-reference/keywords/my-reference.md). Možná budete muset přizpůsobit stávající členy `My` obor názvů, aby lépe odpovídat potřebám vaší aplikace. Vlastnost v objektu `My` obor názvů, který není určen jen pro čtení můžete nastavit na vlastní hodnotu.  
  
 Předpokládejme například, že často používáte `My.User` objekt, který má přístup k aktuální kontext zabezpečení pro uživatele spuštění aplikace. Však vaše společnost používá vlastní uživatelské objekt ke zveřejnění dalších informací a možnosti pro uživatele v rámci společnosti. V tomto scénáři můžete nahradit výchozí hodnota `My.User.CurrentPrincipal` vlastnost s instanci vlastního objektu zabezpečení, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Nastavení `CurrentPrincipal` vlastnost `My.User` změny objektu identitu, pod kterým je aplikace spuštěná. `My.User` Objekt, pak vrátí informace o nově zadaný uživatel.  
  
##  <a name="addingtoobjects"></a> Přidávání členů do mé objekty  
 Typy vrácené z `My.Application` a `My.Computer` jsou definovány jako `Partial` třídy. Proto můžete rozšířit `My.Application` a `My.Computer` objekty ve vytváření `Partial` třídu s názvem `MyApplication` nebo `MyComputer`. Třída nemůže být `Private` třídy. Pokud zadáte jako součást třídy `My` obor názvů, můžete přidat vlastnosti a metody, které budou součástí `My.Application` nebo `My.Computer` objekty.  
  
 Například následující příklad přidá vlastnost s názvem `DnsServerIPAddresses` k `My.Computer` objektu.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> Přidání vlastních objektů do My Namespace  
 I když `My` obor názvů poskytuje řešení pro mnoho běžných programovacích úloh, můžete narazit na úlohy, `My` neřeší oboru názvů. Například aplikace může získat přístup ke službám vlastní adresáře pro data uživatelů nebo vaše aplikace může používat sestavení, které nejsou nainstalované ve výchozím nastavení v jazyce Visual Basic. Můžete rozšířit `My` obor názvů zahrnout vlastní řešení běžných úkolů, které jsou specifické pro vaše prostředí. `My` Oboru názvů lze snadno rozšířit o nové členy rostoucím potřebám aplikace. Kromě toho můžete nasadit vaše `My` rozšíření oboru názvů pro ostatní vývojáři jako šablonu jazyka Visual Basic.  
  
###  <a name="addingtonamespace"></a> Přidávání členů do My Namespace  
 Protože `My` je obor názvů jako jiný obor názvů, můžete přidat nejvyšší úrovně vlastnosti k němu pouze přidáním modulu a určením `Namespace` z `My`. Přidání poznámek ke modul s `HideModuleName` atributu, jak je znázorněno v následujícím příkladu. `HideModuleName` Atribut zajišťuje, že technologie IntelliSense nezobrazí na název modulu, když se zobrazí členy `My` oboru názvů.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Přidat členy do `My` obor názvů, přidejte podle potřeby modulu vlastnosti. Pro každou vlastnost přidán do `My` obor názvů, přidejte soukromé pole typu `ThreadSafeObjectProvider(Of T)`, kde typ je typ vrácený vlastní vlastnosti. V tomto poli se používá k vytvoření instance objektů vláken má být vrácen vlastností voláním `GetInstance` metoda. V důsledku toho každý podproces, který přistupuje k rozšířené vlastnosti obdrží svou vlastní instanci vráceného typu. Následující příklad přidá vlastnost s názvem `SampleExtension` , je typu `SampleExtension` k `My` obor názvů:  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> Přidávání událostí do vlastní objekty  
 Můžete použít `My.Application` objekt, který chcete zpřístupnit události pro vaše vlastní `My` objekty tím, že rozšíří `MyApplication` třídu v `My` oboru názvů. Pro projekty založené na systému Windows, můžete dvakrát kliknout **Můj projekt** uzlu pro svůj projekt v **Průzkumníku řešení**. V jazyce Visual Basic **Návrhář projektu**, klikněte `Application` a pak klikněte `View Application Events` tlačítko. Vytvoří se nový soubor s názvem ApplicationEvents.vb. Obsahuje následující kód pro rozšíření `MyApplication` třídy.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Přidáním obslužných rutin událostí pro vaše vlastní `My` objekty tak, že přidáte vlastní obslužné rutiny na `MyApplication` třídy. Vlastní události umožňují přidejte kód, který se spustí, když obslužné rutiny události přidávat, odebírat, nebo je vyvolána událost. Všimněte si, že `AddHandler` kód pro vlastní události spustí jenom v případě, že kód není přidán uživatelem se zpracovat událost. Zvažte například, který `SampleExtension` má objekt z předchozí části `Load` událost, která chcete přidat vlastní obslužnou rutinu pro. Následující příklad kódu ukazuje vlastní obslužnou rutinu, s názvem `SampleExtensionLoad` , bude volána, když `My.SampleExtension.Load` dojde k události. Když je přidán kód pro zpracování nové `My.SampleExtensionLoad` událostí, `AddHandler` součástí tohoto kódu vlastní události se spustí. `MyApplication_SampleExtensionLoad` Metoda je zahrnuta v příkladu kódu k zobrazení příkladu obslužnou rutinu události, která zpracovává `My.SampleExtensionLoad` událostí. Všimněte si, že `SampleExtensionLoad` událostí bude k dispozici, když vyberete **Moje události aplikace** možnost v seznamu levém rozevíracím výše editoru kódu při úpravách souboru ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> Pokyny pro návrh  
 Když budete vyvíjet rozšíření pro `My` obor názvů, pomocí následujících pokynů můžete minimalizovat náklady na údržbu komponent rozšíření.  
  
-   **Zahrnout pouze logiku rozšíření.** Logika obsažená v `My` obsahovat pouze kód, který je nutný k zpřístupnění požadované funkce v rozšíření oboru názvů `My` oboru názvů. Vzhledem k tomu, že toto rozšíření se bude nacházet v projektech uživatele jako zdrojový kód, aktualizování komponent rozšíření způsobuje vysoké náklady na údržbu a je nutno Pokud je to možné.  
  
-   **Minimalizujte předpoklady projekt.** Při vytváření vašeho rozšíření `My` obor názvů, Nepředpokládejte sadu odkazů, importy na úrovni projektu nebo specifické nastavení kompilátoru (například `Option Strict` off). Místo toho minimalizovat závislosti a plnému určení všechny odkazy na typ pomocí `Global` – klíčové slovo. Také se ujistěte, že se rozšíření zkompiluje s `Option Strict` na minimalizovat chyb rozšíření.  
  
-   **Izolujte kód rozšíření.** Umístění kód do jednoho souboru umožňuje rozšíření snadno nasadit jako šablonu položky Visual Studio. Další informace najdete v tématu "Balení a nasazení rozšíření" dál v tomto tématu. Umístění všech `My` rozšíření oboru v jednom souboru nebo do samostatné složky v projektu také pomohou uživatelům najít `My` rozšíření oboru názvů.  
  
##  <a name="designing"></a> Navrhování knihovny tříd pro Moje  
 Je tomu u většiny objektů a modelů, některé vzory návrhu dobře fungovaly v `My` obor názvů a jiné nikoli. Při navrhování rozšíření `My` obor názvů, zvažte následující zásady:  
  
-   **Bezstavové metody.** Metody v `My` obor názvů by měl poskytovat kompletního řešení pro konkrétní úlohu. Ověřili, jestli hodnoty parametrů, které jsou předaný metodě poskytovat všechny vstupy potřebné k dokončení konkrétní úlohy. Vyhněte se vytváření metody, které jsou závislé na předchozím stavu, jako je otevření připojení k prostředkům.  
  
-   **Globální instance.** Jediný stav, který se udržuje v `My` obor názvů je globální pro projekt. Například `My.Application.Info` zapouzdří stav, který je sdílen v celé aplikaci.  
  
-   **Jednoduché typy parametrů.** Zjednodušení vyhnout komplexních typů parametrů. Místo toho vytvořte metody, které buď přijímají žádný vstupní parametr nebo které přebírají jednoduché vstupní typy, například řetězce, primitivní typy a tak dále.  
  
-   **Metody vytváření.** Některé typy nutně obtížně se vytvořit instanci. Poskytování metodami pro vytváření jako rozšíření `My` obor názvů umožňuje snadno zjištění a použití typů, které spadají do této kategorie patří. Je například metoda factory, která funguje dobře `My.Computer.FileSystem.OpenTextFileReader`. Nejsou k dispozici v rozhraní .NET Framework několik typů datového proudu. Zadáním textových souborů konkrétně `OpenTextFileReader` pomáhá uživateli pochopit, které datový proud použít.  
  
 Tyto pokyny nejsou v konfliktu zásady obecné designu pro knihovny tříd. Namísto toho jsou doporučení, která jsou optimalizována pro vývojáře, kteří používají Visual Basic a `My` oboru názvů. Obecné návrhu zásad pro vytvoření knihovny tříd, najdete v části [pokynů pro návrh Framework](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a> Balení a nasazení rozšíření  
 Můžete zahrnout `My` rozšíření oboru názvů v šablona projektu sady Visual Studio, nebo můžete vytvořit balíček rozšíření a nasadit jej jako šablonu položky Visual Studio. Když vytvoříte balíček vaší `My` rozšíření oboru názvů jako šablonu položky Visual Studio, můžete využít další funkce poskytované jazyka Visual Basic. Tyto funkce umožňují zahrnout rozšíření, když na projekt odkazuje na konkrétní sestavení nebo umožnění uživatelům explicitně přidat vaše `My` rozšíření oboru názvů pomocí **Moje rozšíření** stránky jazyka Visual Basic Návrhář projektu.  
  
 Podrobnosti o tom, jak nasadit `My` rozšíření oboru názvů, najdete v části [balení a nasazení Moje rozšíření vlastní](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Viz také  
 [Balení a nasazení vlastních rozšíření oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
