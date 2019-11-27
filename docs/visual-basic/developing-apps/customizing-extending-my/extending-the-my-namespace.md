---
title: Rozšíření oboru názvů My
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330323"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozšíření oboru názvů `My` v Visual Basic

Obor názvů `My` v Visual Basic zpřístupňuje vlastnosti a metody, které vám umožní snadno využít sílu .NET Framework. Obor názvů `My` zjednodušuje běžné programové problémy, často zkracuje obtížné úlohu na jeden řádek kódu. Kromě toho je obor názvů `My` plně rozšiřitelný, takže můžete přizpůsobit chování `My` a přidat nové služby do své hierarchie, abyste je přizpůsobili konkrétním potřebám aplikací. Toto téma popisuje, jak přizpůsobit stávající členy `My` oboru názvů a jak přidat vlastní třídy do oboru názvů `My`.

## <a name="customizing-existing-my-namespace-members"></a>Přizpůsobení stávajících `My` členů oboru názvů

Obor názvů `My` v Visual Basic zpřístupňuje často používané informace o vaší aplikaci, počítači a dalších. Úplný seznam objektů v oboru názvů `My` naleznete v části [můj odkaz](../../language-reference/keywords/my-reference.md). Je možné, že budete muset přizpůsobit stávající členy `My` oboru názvů tak, aby lépe odpovídaly potřebám vaší aplikace. Vlastnost objektu v oboru názvů `My`, která není jen pro čtení, může být nastavena na vlastní hodnotu.

Předpokládejme například, že často používáte objekt `My.User` pro přístup k aktuálnímu kontextu zabezpečení pro uživatele, který spouští vaši aplikaci. Vaše společnost ale používá vlastní objekt uživatele k vystavování dalších informací a možností pro uživatele v rámci společnosti. V tomto scénáři můžete nahradit výchozí hodnotu vlastnosti `My.User.CurrentPrincipal` instance vlastního objektu zabezpečení, jak je znázorněno v následujícím příkladu:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

Nastavením vlastnosti `CurrentPrincipal` u objektu `My.User` se změní identita, pod kterou je aplikace spuštěná. Objekt `My.User` zase vrátí informace o nově zadaném uživateli.
  
## <a name="adding-members-to-my-objects"></a>Přidávání členů do objektů `My`

Typy vrácené z `My.Application` a `My.Computer` jsou definovány jako třídy `Partial`. Proto můžete objekty `My.Application` a `My.Computer` rozšíříte tak, že vytvoříte třídu `Partial` s názvem `MyApplication` nebo `MyComputer`. Třída nemůže být třída `Private`. Pokud zadáte třídu jako součást oboru názvů `My`, můžete přidat vlastnosti a metody, které budou zahrnuty do objektů `My.Application` nebo `My.Computer`.

Následující příklad přidá vlastnost s názvem `DnsServerIPAddresses` do objektu `My.Computer`:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Přidání vlastních objektů do oboru názvů `My`

I když obor názvů `My` poskytuje řešení pro mnoho běžných programovacích úloh, může dojít k úlohám, které obor názvů `My` neřeší. Vaše aplikace může například získat přístup k vlastním adresářovým službám pro uživatelská data nebo vaše aplikace může používat sestavení, která nejsou ve výchozím nastavení nainstalovaná pomocí Visual Basic. Obor názvů `My` můžete zvětšit tak, aby zahrnoval vlastní řešení běžných úloh, které jsou specifické pro vaše prostředí. Obor názvů `My` lze snadno rozšířit a přidat nové členy pro splnění rostoucích potřeb aplikací. Kromě toho můžete nasadit rozšíření `My` oboru názvů jiným vývojářům jako šablonu Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Přidávání členů do oboru názvů `My`

Vzhledem k tomu, že `My` je obor názvů stejným způsobem jako jakýkoli jiný obor názvů, můžete do něj přidat vlastnosti nejvyšší úrovně pouhým přidáním modulu a určením `Namespace` `My`. Přihlaste se k modulu pomocí atributu `HideModuleName`, jak je znázorněno v následujícím příkladu. Atribut `HideModuleName` zajišťuje, že technologie IntelliSense nebude zobrazovat název modulu, když zobrazuje členy `My` oboru názvů.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Chcete-li přidat členy do oboru názvů `My`, přidejte do modulu vlastnosti podle potřeby. Pro každou vlastnost přidanou do oboru názvů `My` přidejte soukromé pole typu `ThreadSafeObjectProvider(Of T)`, kde typ je typ vrácený vaší vlastní vlastností. Toto pole se používá k vytvoření instancí objektů bezpečných pro přístup z více vláken, které jsou vráceny vlastností voláním metody `GetInstance`. V důsledku toho každé vlákno, které přistupuje k rozšířené vlastnosti, obdrží svou vlastní instanci vráceného typu. Následující příklad přidá vlastnost s názvem `SampleExtension`, která je typu `SampleExtension` na obor názvů `My`:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Přidávání událostí do vlastních objektů `My`

Objekt `My.Application` lze použít k vystavení událostí pro vlastní objekty `My` rozšířením `MyApplication` částečné třídy v oboru názvů `My`. Pro projekty založené na systému Windows můžete dvakrát kliknout na uzel **můj projekt** v pro projekt v **Průzkumník řešení**. V **Návrháři projektu**Visual Basic klikněte na kartu **aplikace** a pak klikněte na tlačítko **Zobrazit události aplikace** . Vytvoří se nový soubor s názvem *ApplicationEvents. vb* . Obsahuje následující kód pro rozšíření `MyApplication` třídy:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Můžete přidat obslužné rutiny událostí pro vlastní objekty `My` přidáním vlastních obslužných rutin událostí do třídy `MyApplication`. Vlastní události umožňují přidat kód, který se spustí při přidání, odebrání nebo vyvolání obslužné rutiny události. Všimněte si, že kód `AddHandler` vlastní události se spustí pouze v případě, že uživatel přidá kód pro zpracování události. Například zvažte, že objekt `SampleExtension` z předchozí části obsahuje událost `Load`, do které chcete přidat vlastní obslužnou rutinu události pro. Následující příklad kódu ukazuje vlastní obslužnou rutinu události s názvem `SampleExtensionLoad`, která bude vyvolána při výskytu události `My.SampleExtension.Load`. Když je přidán kód pro zpracování nové události `My.SampleExtensionLoad`, je provedena `AddHandler` část tohoto vlastního kódu události. Metoda `MyApplication_SampleExtensionLoad` je obsažena v příkladu kódu k zobrazení příkladu obslužné rutiny události, která zpracovává událost `My.SampleExtensionLoad`. Všimněte si, že událost `SampleExtensionLoad` bude k dispozici po výběru možnosti **Moje události aplikace** v levém rozevíracím seznamu nad Editor kódu při úpravách souboru *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Pokyny pro návrh

Při vývoji rozšíření na obor názvů `My` použijte následující pokyny, které vám pomohou minimalizovat náklady na údržbu vašich komponent rozšíření:

- **Zahrňte pouze logiku rozšíření.** Logika obsažená v rozšíření `My` oboru názvů by měla obsahovat pouze kód, který je nezbytný k vystavení požadované funkce v oboru názvů `My`. Vzhledem k tomu, že se rozšíření bude nacházet v uživatelských projektech jako zdrojový kód, aktualizace komponenty rozšíření má za následek vysoké náklady na údržbu a je třeba se jim vyhnout, pokud je to možné.
- **Minimalizujte předpoklady projektu.** Při vytváření rozšíření oboru názvů `My` nemusíte předpokládat sadu odkazů, import na úrovni projektu ani specifická nastavení kompilátoru (například `Option Strict` vypnuto). Místo toho minimalizujte závislosti a plně zařaďte všechny odkazy na typy pomocí klíčového slova `Global`. Také se ujistěte, že se rozšíření zkompiluje s `Option Strict` pro minimalizaci chyb v rozšíření.
- **Izolujte kód rozšíření.** Vložení kódu do jediného souboru způsobí, že se rozšíření dá snadno nasadit jako šablona položky Visual Studio. Další informace najdete v části "balení a nasazování rozšíření" dále v tomto tématu. Umístění veškerého kódu rozšíření `My` oboru názvů do jednoho souboru nebo samostatné složky v projektu pomůže uživatelům také najít `My` oboru názvů.

## <a name="designing-class-libraries-for-my"></a>Návrh knihoven tříd pro `My`

Stejně jako u většiny objektových modelů mají některé vzory návrhu v oboru názvů `My` dobře fungovat a jiné ne. Při návrhu rozšíření na obor názvů `My` Vezměte v úvahu následující principy:

- **Bezstavové metody.** Metody v oboru názvů `My` by měly pro určitý úkol poskytnout kompletní řešení. Zajistěte, aby hodnoty parametrů předané metodě poskytovaly veškerý vstup potřebný k dokončení konkrétního úkolu. Vyhněte se vytváření metod, které spoléhají na předchozí stav, jako je například otevření připojení k prostředkům.
- **Globální instance.** Jediný stav, který je udržován v oboru názvů `My`, je globální pro projekt. Například `My.Application.Info` zapouzdřuje stav, který je sdílen v celé aplikaci.
- **Jednoduché typy parametrů.** Zachovejte věci jednoduché, protože se vyhnete složitým typům parametrů. Místo toho vytvořte metody, které buď nevyužívají vstup parametrů, nebo které přebírají jednoduché vstupní typy, jako jsou například řetězce, primitivní typy a tak dále.
- **Metody pro vytváření.** Vytváření instancí je nutně obtížné u některých typů. Poskytování produkčních metod jako rozšíření oboru názvů `My` umožňuje snadněji zjišťovat a využívat typy, které spadají do této kategorie. Příklad metody továrny, která funguje dobře, je `My.Computer.FileSystem.OpenTextFileReader`. V .NET Framework je k dispozici několik typů datových proudů. Zadáním textových souborů konkrétně `OpenTextFileReader` pomůže uživateli pochopit, který datový proud chcete použít.

Tyto pokyny nevylučují obecné principy návrhu pro knihovny tříd. Místo toho jsou doporučení optimalizovaná pro vývojáře, kteří používají Visual Basic a obor názvů `My`. Obecné principy navrhování pro vytváření knihoven tříd naleznete v tématu [pokyny pro návrh rozhraní](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Balení a nasazení rozšíření

Do šablony projektu sady Visual Studio můžete zahrnout `My` rozšíření oboru názvů, nebo můžete zabalit rozšíření a nasadit je jako šablonu položky sady Visual Studio. Když zabalíte rozšíření oboru názvů `My` jako šablonu položky sady Visual Studio, můžete využít výhod dalších funkcí poskytovaných Visual Basic. Tyto možnosti umožňují zahrnout rozšíření, když projekt odkazuje na konkrétní sestavení, nebo povolit uživatelům explicitní přidání `My`ho rozšíření oboru názvů pomocí stránky **Moje rozšíření** v návrháři projektu Visual Basic.

Podrobnosti o tom, jak nasadit rozšíření oboru názvů `My`, najdete v tématu [balení a nasazení vlastních rozšíření](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Viz také:

- [Balení a nasazení vlastních rozšíření oboru názvů My](packaging-and-deploying-custom-my-extensions.md)
- [Rozšíření aplikačního modelu jazyka Visual Basic](extending-the-visual-basic-application-model.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](customizing-which-objects-are-available-in-my.md)
- [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../language-reference/modifiers/partial.md)
