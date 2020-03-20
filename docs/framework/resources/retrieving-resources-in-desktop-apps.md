---
title: Načítání prostředků v aplikacích klasické pracovní plochy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
ms.openlocfilehash: 17795db2cdec419a31fe862793c88506f9535ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180451"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Načítání prostředků v aplikacích klasické pracovní plochy

Při práci s lokalizovanými prostředky v desktopových aplikacích rozhraní .NET Framework byste měli v ideálním případě zabalit prostředky pro výchozí nebo neutrální jazykovou verzi s hlavním sestavením a vytvořit samostatné satelitní sestavení pro každý jazyk nebo jazykovou verzi, kterou vaše aplikace podporuje. Potom můžete použít <xref:System.Resources.ResourceManager> třídu, jak je popsáno v další části pro přístup k pojmenované prostředky. Pokud se rozhodnete nevložit prostředky do hlavního sestavení a satelitní sestavení, můžete také přistupovat k binárním souborům .resources přímo, jak je popsáno v části [Načítání prostředků ze souborů .resources](#from_file) dále v tomto článku.  Informace o načtení prostředků v aplikacích pro Windows 8.x Store najdete [v tématu Vytváření a načítání prostředků v aplikacích pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140)).  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Načítání prostředků ze sestavení  
 Třída <xref:System.Resources.ResourceManager> poskytuje přístup k prostředkům v době běhu. Metodu <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> použijete k načtení <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> prostředků řetězce a metody nebo k načtení prostředků bez řetězce. Každá metoda má dvě přetížení:  
  
- Přetížení, jehož jeden parametr je řetězec, který obsahuje název prostředku. Metoda se pokusí načíst tento prostředek pro aktuální jazykovou verzi vlákna. Další informace naleznete <xref:System.Resources.ResourceManager.GetString%28System.String%29>v <xref:System.Resources.ResourceManager.GetObject%28System.String%29>tématu , , a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
- Přetížení, které má dva parametry: řetězec obsahující název prostředku <xref:System.Globalization.CultureInfo> a objekt, který představuje jazykovou verzi, jejíž prostředek má být načten. Pokud nelze najít sadu prostředků pro tuto jazykovou verzi, správce prostředků použije záložní pravidla k načtení příslušného prostředku. Další informace naleznete <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>v <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>tématu , , a <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Správce prostředků používá záložní proces prostředků k řízení, jak aplikace načítá prostředky specifické pro jazykovou verzi. Další informace naleznete v části Proces záložního prostředku v [tématu Balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md). Informace o vytváření instancí objektu <xref:System.Resources.ResourceManager> naleznete v části Vytvoření vytváření instancí objektu ResourceManager v tématu <xref:System.Resources.ResourceManager> kurzu.  
  
### <a name="retrieving-string-data-an-example"></a>Načítání řetězcových dat: Příklad  
 Následující příklad volá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodu k načtení prostředků řetězce aktuální jazykové verze uhlavního žena. Obsahuje neutrální řetězec prostředek pro jazykovou verzi angličtiny (Spojené státy) a lokalizované prostředky pro francouzské (Francie) a ruské (Rusko) jazykové verze. Následující prostředek angličtiny (Spojené státy) je v souboru s názvem Strings.txt:  
  
```text
TimeHeader=The current time is  
```  
  
 Prostředek francouzštiny (Francie) je v souboru s názvem Strings.fr-FR.txt:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Ruský (Rusko) zdroj je v souboru s názvem Strings.ru-RU-txt:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Zdrojový kód pro tento příklad, který je v souboru s názvem GetString.cs pro c# verze kódu a GetString.vb pro verzi jazyka Visual Basic, definuje pole řetězců, které obsahuje název čtyř kultur: tři jazykové verze, pro které jsou k dispozici prostředky a španělské (Španělsko) jazykové verze. Smyčka, která se provede pětkrát náhodně vybere jednu z těchto <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> kultur a přiřadí ji vlastnostem a. Potom volá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodu k načtení lokalizovaného řetězce, který se zobrazí spolu s denní dobou.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Následující dávkový soubor (.bat) zkompiluje příklad a generuje satelitní sestavení v příslušných adresářích. Příkazy jsou k dispozici pro jazyk C# a kompilátor. V jazyce `csc` Visual `vbc`Basic `GetString.cs` změňte na . a změňte na `GetString.vb`.  
  
```console
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Pokud je aktuální jazyková verze ui španělština (Španělsko), všimněte si, že v příkladu se zobrazí prostředky anglického jazyka, protože španělské jazykové prostředky nejsou k dispozici a angličtina je výchozí jazykovou verzi v příkladu.  
  
### <a name="retrieving-object-data-two-examples"></a>Načítání dat objektů: Dva příklady  
 Metody <xref:System.Resources.ResourceManager.GetObject%2A> a <xref:System.Resources.ResourceManager.GetStream%2A> můžete použít k načtení dat objektu. To zahrnuje primitivní datové typy, serializovatelné objekty a objekty, které jsou uloženy v binárním formátu (například obrázky).  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metodu k načtení rastrového obrázku, který se používá v úvodním okně aplikace. Následující zdrojový kód v souboru s názvem CreateResources.cs (pro C#) nebo CreateResources.vb (pro visual basic) generuje soubor Resx, který obsahuje serializovaný obraz. V tomto případě je obraz načten ze souboru s názvem SplashScreen.jpg; můžete upravit název souboru a nahradit tak vlastní obrázek.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Následující kód načte prostředek a zobrazí <xref:System.Windows.Forms.PictureBox> bitovou kopii v ovládacím prvku.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 K vytvoření příkladu jazyka C# můžete použít následující dávkový soubor. V jazyce `csc` Visual `vbc`Basic změňte na a změňte příponu souboru zdrojového kódu z `.cs` na . `.vb`  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodu k rekonstrukci vlastního objektu. Příklad obsahuje soubor zdrojového kódu s názvem UIElements.cs (UIElements.vb pro `PersonTable`visual basic), který definuje následující strukturu s názvem . Tato struktura je určena pro použití rutinou zobrazení obecné tabulky, která zobrazuje lokalizované názvy sloupců tabulky. Všimněte `PersonTable` si, že <xref:System.SerializableAttribute> struktura je označenatributem.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Následující kód ze souboru s názvem CreateResources.cs (CreateResources.vb pro visual basic) vytvoří soubor prostředků XML s `PersonTable` názvem UIResources.resx, který ukládá název tabulky a objekt, který obsahuje informace pro aplikaci, která je lokalizována pro anglický jazyk.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Následující kód v souboru zdrojového kódu s názvem GetObject.cs (GetObject.vb) načte prostředky a zobrazí je do konzoly.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Můžete vytvořit potřebný soubor prostředků a sestavení a spustit aplikaci spuštěním následujícídávkový soubor. Je nutné `/r` použít možnost poskytnout Resgen.exe s odkazem na UIElements.dll `PersonTable` tak, aby přístup k informacím o struktuře. Pokud používáte C#, nahraďte `vbc` název `csc`kompilátoru písmenem a `.vb` nahraďte rozšíření . `.cs`  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Podpora správy verzí pro satelitní sestavení  
 Ve výchozím nastavení <xref:System.Resources.ResourceManager> při načtení požadovaných prostředků objektu hledá satelitní sestavení s čísly verzí, která odpovídají číslu verze hlavního sestavení. Po nasazení aplikace můžete chtít aktualizovat hlavní sestavení nebo satelitní sestavení konkrétních prostředků. Rozhraní .NET Framework poskytuje podporu pro správu verzí hlavní sestavení a satelitní sestavení.  
  
 Atribut <xref:System.Resources.SatelliteContractVersionAttribute> poskytuje podporu správy verzí pro hlavní sestavení. Zadání tohoto atributu v hlavním sestavení aplikace umožňuje aktualizovat a znovu nasadit hlavní sestavení bez aktualizace jeho satelitní sestavení. Po aktualizaci hlavního sestavení, zvýšení číslo verze hlavního sestavení, ale ponechat číslo verze satelitní smlouvy beze změny. Když správce prostředků načte požadované prostředky, načte verzi satelitního sestavení určenou tímto atributem.  
  
 Sestavení zásad aplikace Publisher poskytují podporu pro správu verzí satelitních sestavení. Můžete aktualizovat a znovu nasadit satelitní sestavení bez aktualizace hlavního sestavení. Po aktualizaci satelitního sestavení větev jeho čísla verze a jeho odeslání se sestavením zásad vydavatele. V sestavení zásad vydavatele určete, že nové satelitní sestavení je zpětně kompatibilní s předchozí verzí. Správce prostředků použije <xref:System.Resources.SatelliteContractVersionAttribute> atribut k určení verze satelitního sestavení, ale zavaděč sestavení se bude vázat na verzi satelitního sestavení určenou zásadami vydavatele. Další informace o sestaveních zásad vydavatele naleznete [v tématu Vytvoření souboru zásad aplikace Publisher](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Chcete-li povolit plnou podporu správy verzí sestavení, doporučujeme nasadit sestavení se silným názvem v [globální mezipaměti sestavení](../app-domains/gac.md) a nasadit sestavení, která nemají silné názvy v adresáři aplikace. Pokud chcete nasadit sestavení se silným názvem v adresáři aplikace, nebudete moci při aktualizaci sestavení povýšit číslo verze satelitního sestavení. Místo toho je nutné provést aktualizaci na místě, kde nahradíte existující kód aktualizovaným kódem a zachováte stejné číslo verze. Chcete-li například aktualizovat verzi 1.0.0.0 satelitního sestavení s plně zadaným názvem sestavení "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a", přepište ji aktualizovaným souborem myApp.resources.dll, který byl kompilován se stejným, plně zadaným názvem sestavení "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a". Všimněte si, že použití aktualizací na místě na soubory satelitní sestavení ztěžuje aplikaci přesně určit verzi satelitního sestavení.  
  
 Další informace o správu verzí sestavení naleznete v [tématech Správa verzí sestavení](../../standard/assembly/versioning.md) a [Jak runtime loizuje sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>Načítání zdrojů ze souborů .resources  
 Pokud se rozhodnete nenasazovat prostředky v satelitních <xref:System.Resources.ResourceManager> sestaveních, můžete stále použít objekt pro přímý přístup k prostředkům ze souborů .resources. Chcete-li to provést, je nutné správně nasadit soubory .resources. Potom použijete <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metodu k vytvoření <xref:System.Resources.ResourceManager> instance objektu a určíte adresář, který obsahuje samostatné soubory .resources.  
  
### <a name="deploying-resources-files"></a>Nasazení souborů .resources  
 Při vložení souborů .resources do sestavení aplikace a satelitních sestavení má každé satelitní sestavení stejný název souboru, ale je umístěno do podadresáře, který odráží jazykovou verzi satelitního sestavení. Naproti tomu při přímém přístupu k prostředkům ze souborů .resources můžete umístit všechny soubory .resources do jednoho adresáře, obvykle podadresáře adresáře aplikace. Název výchozího souboru prostředků aplikace se skládá pouze z kořenového názvu bez označení jeho jazykové verze (například strings.resources). Prostředky pro každou lokalizovanou jazykovou verzi jsou uloženy v souboru, jehož název se skládá z kořenového názvu následovaného jazykovou verzí (například strings.ja.resources nebo strings.de-DE.resources).

 Následující obrázek znázorňuje, kde by měly být umístěny soubory prostředků ve struktuře adresářů. Poskytuje také konvence pojmenování pro soubory .resource.  

 ![Obrázek, který znázorňuje hlavní adresář aplikace.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Použití Správce prostředků  
 Po vytvoření prostředků a jejich umístění do příslušného <xref:System.Resources.ResourceManager> adresáře vytvoříte objekt <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> pro použití prostředků voláním metody. První parametr určuje kořenový název výchozího souboru prostředků aplikace (to by byly "řetězce" pro příklad v předchozí části). Druhý parametr určuje umístění prostředků ("Zdroje" pro předchozí příklad). Třetí parametr určuje <xref:System.Resources.ResourceSet> implementaci, která má být používána. Pokud je `null`třetí parametr , <xref:System.Resources.ResourceSet> použije se výchozí doba runtime.  
  
> [!NOTE]
> Nenasazujte ASP.NET aplikace pomocí samostatných souborů .resources. To může způsobit problémy se zamykáním a přeruší nasazení XCOPY. Doporučujeme nasadit ASP.NET prostředky v satelitních sestaveních. Další informace naleznete [v tématu ASP.NET Přehled zdrojů webových stránek](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po <xref:System.Resources.ResourceManager> vytvoření instance objektu použijete <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>a <xref:System.Resources.ResourceManager.GetStream%2A> metody, jak je popsáno výše načíst prostředky. Načítání prostředků přímo ze souborů .resources se však liší od načítání vložených prostředků z sestavení. Při načtení prostředků ze souborů <xref:System.Resources.ResourceManager.GetString%28System.String%29> <xref:System.Resources.ResourceManager.GetObject%28System.String%29>.resources <xref:System.Resources.ResourceManager.GetStream%28System.String%29> načíst , a metody vždy načíst výchozí jazykovou verzi prostředky bez ohledu na aktuální jazykovou verzi. Chcete-li načíst prostředky aktuální jazykové verze aplikace nebo konkrétní jazykové <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29> <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>verze, <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> musíte volat , nebo metodu a určit jazykovou verzi, jejíž prostředky mají být načteny. Chcete-li načíst prostředky aktuální jazykové verze, zadejte hodnotu vlastnosti <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> `culture` jako argument. Pokud správce prostředků nemůže načíst prostředky aplikace `culture`, použije standardní záložní pravidla prostředků k načtení příslušných prostředků.  
  
### <a name="an-example"></a>Příklad  
 Následující příklad ukazuje, jak správce prostředků načítá prostředky přímo ze souborů .resources. Příklad se skládá ze tří souborů prostředků založených na textu pro jazykové verze Angličtina (Spojené státy), Francouzština (Francie) a Ruština (Rusko). Angličtina (Spojené státy) je výchozí jazyková verze příkladu. Jeho prostředky jsou uloženy v následujícím souboru s názvem Strings.txt:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Prostředky pro francouzskou (francouzskou) jazykovou verzi jsou uloženy v následujícím souboru s názvem Strings.fr-FR.txt:  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Prostředky pro ruskou (ruskou) jazykovou verzi jsou uloženy v následujícím souboru s názvem Strings.ru-RU.txt:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Následuje zdrojový kód pro příklad. Příklad instance objekty <xref:System.Globalization.CultureInfo> pro angličtinu (Spojené státy), angličtina (Kanada), francouzština (Francie) a ruské (Rusko) jazykové verze a každý aktuální jazykovou verzi. Metoda <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> pak poskytuje hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti `culture` jako argument pro načtení příslušných prostředků specifických pro jazykovou verzi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Můžete zkompilovat verzi C# v příkladu spuštěním následující dávkový soubor. Pokud používáte jazyk Visual `csc` Basic, nahraďte `vbc`pomocí aplikace a nahraďte `.cs` rozšíření . `.vb`  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Resources.ResourceManager>
- [Prostředky v aplikacích klasické pracovní plochy](index.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Vytváření a načítání prostředků v aplikacích pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))
