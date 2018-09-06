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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1be7120b9bff5c51141a1eac80051c4b464433aa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801551"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Načítání prostředků v aplikacích klasické pracovní plochy
Při práci s lokalizované prostředky v desktopových aplikacích rozhraní .NET Framework by měl v ideálním případě balíček prostředků pro výchozí nebo neutrální jazykovou verzi s hlavním sestavením a vytvořte samostatné satelitní sestavení pro každý jazyk nebo jazykovou verzi, která vaše aplikace podporuje. Pak můžete použít <xref:System.Resources.ResourceManager> třídy, jak je popsáno v další části a přístup k pojmenovaným prostředkům. Pokud se rozhodnete vložit prostředky do hlavního sestavení a satelitní sestavení, se dá dostat taky binárních souborů .resources přímo, jak je popsáno v části [načítání prostředků ze souborů .resources](#from_file) dále v tomto článek.  Pro načtení prostředků v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, najdete v článku [vytváření a načítání prostředků v aplikacích pro Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674) Windows Dev Center.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Načítání prostředků ze sestavení  
 <xref:System.Resources.ResourceManager> Třídě poskytuje přístup k prostředkům v době běhu. Můžete použít <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody k získání řetězcové prostředky a <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> nebo <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> metodu pro načtení neřetězcové prostředky. Každá z metod má dvě přetížení:  
  
-   Přetížení jehož jediný parametr je řetězec, který obsahuje název prostředku. Metoda se pokusí načíst tento prostředek pro aktuální jazykovou verzi vlákna. Další informace najdete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
-   Přetížení, která má dva parametry: řetězec obsahující název prostředku a s <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, jejíž prostředek má být načtena. Pokud prostředek pro nastavené, nebyl nalezen jazykovou verzi, správce prostředků používá pravidla pro použití náhradní lokality k načtení odpovídající prostředek. Další informace najdete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Proces získávání náhradních prostředků resource Manageru používá k řízení, jak aplikace načítá prostředky specifické pro jazykovou verzi. Další informace najdete v tématu v části "Proces záložního prostředku" [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Informace o vytvoření instance <xref:System.Resources.ResourceManager> objektu, naleznete v části "Vytvoření instance objektu ResourceManager" <xref:System.Resources.ResourceManager> třídě.  
  
### <a name="retrieving-string-data-an-example"></a>Načítání dat řetězce: Příklad  
 Následující příklad volá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metody k získání řetězcové prostředky aktuální jazykové verze uživatelského rozhraní. Francouzština (Francie) a jazykové verze ruština (Rusko) obsahuje prostředek řetězce neutrální jazykové verze Angličtina (Spojené státy) a lokalizované prostředky. Následující prostředek Angličtina (Spojené státy) je do souboru s názvem Strings.txt:  
  
```  
TimeHeader=The current time is  
```  
  
 Francouzština (Francie) prostředků je do souboru s názvem Strings.fr-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Ruština (Rusko) prostředků je do souboru s názvem Strings.ru-RU-txt:  
  
```  
TimeHeader=Текущее время —  
```  
  
 Zdrojový kód pro tento příklad, který je do souboru s názvem GetString.cs pro C# verzi kódu a GetString.vb pro verze jazyka Visual Basic, definuje pole řetězců obsahující název jazykové verze čtyři: tři jazykové verze, pro které prostředky jsou k dispozici a Španělština (Španělsko) jazykovou verzi. Smyčku, která spustí pětkrát náhodně vybere jeden z těchto jazykové verze a přiřadí ji k <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti. Poté zavolá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodu pro načtení lokalizované řetězce, který se zobrazí spolu s denní dobu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Následující dávkový soubor (BAT) zkompiluje v příkladu a generuje satelitní sestavení v příslušné adresáře. Příkazy jsou k dispozici pro jazyk C# a kompilátoru. V jazyce Visual Basic změnit `csc` k `vbc`a změnit `GetString.cs` k `GetString.vb`.  
  
```  
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Pokud je aktuální jazyková verze uživatelského rozhraní španělština (Španělsko), mějte na paměti, že v příkladu se zobrazí anglické jazykové prostředky, protože španělštiny prostředky nejsou k dispozici a je v příkladu výchozí jazykovou verzi angličtina.  
  
### <a name="retrieving-object-data-two-examples"></a>Načítání dat objektu: Dva příklady  
 Můžete použít <xref:System.Resources.ResourceManager.GetObject%2A> a <xref:System.Resources.ResourceManager.GetStream%2A> metody pro načtení dat objektu. To zahrnuje primitivní datové typy serializovatelné objekty a objekty, které jsou uloženy v binárním formátu (jako jsou obrázky).  
  
 V následujícím příkladu <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metodu pro načtení rastrový obrázek, který se používá v aplikaci prvku otevřete úvodní okno. Tento zdrojový kód do souboru s názvem CreateResources.cs (pro C#) nebo CreateResources.vb (pro jazyk Visual Basic) generuje soubor .resx, který obsahuje serializovaná bitovou kopii. V takovém případě bude obrázek načten ze souboru s názvem SplashScreen.jpg; můžete upravit název souboru nahraďte vlastní image.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Následující kód načte prostředek a zobrazí obraz v <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Následující soubor služby batch můžete použít k vytvoření příkladu jazyka C#. V jazyce Visual Basic změnit `csc` k `vbc`a změňte příponu souboru se zdrojovým kódem z `.cs` k `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 V následujícím příkladu <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodu pro deserializaci vlastních objektů. Příklad obsahuje soubor zdrojového kódu s názvem UIElements.cs (UIElements.vb v jazyce Visual Basic), který definuje následující strukturu s názvem `PersonTable`. Tato struktura je určena pro použití podle rutinu zobrazení obecná tabulka, která se zobrazí lokalizované názvy sloupců tabulky. Všimněte si, že `PersonTable` struktura je označena pomocí <xref:System.SerializableAttribute> atribut.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Následující kód ze souboru s názvem CreateResources.cs (CreateResources.vb v jazyce Visual Basic) vytvoří soubor prostředků jazyka XML s názvem UIResources.resx uchovávající název tabulky a `PersonTable` objekt, který obsahuje informace pro aplikace, který je lokalizován pro Anglický jazyk.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Následující kód v souboru zdrojového kódu s názvem GetObject.cs (GetObject.vb) pak načte prostředky a zobrazí je do konzoly.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Můžete vytvářet nezbytné zdrojového souboru a sestavení a spuštění aplikace pomocí provádí následující dávkový soubor. Je nutné použít `/r` možnost slouží k poskytování Resgen.exe s odkazem na UIElements.dll tak, aby se přístup k informacím o `PersonTable` struktury. Pokud používáte C#, nahraďte `vbc` kompilátoru název s `csc`a nahraďte `.vb` rozšíření s `.cs`.  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Podpora verzí satelitních sestavení  
 Ve výchozím nastavení když <xref:System.Resources.ResourceManager> objekt načte požadované prostředky, vypadá pro satelitní sestavení, které mají čísla verzí, které odpovídají číslu verze hlavní sestavení. Když nasadíte aplikaci, můžete chtít aktualizovat hlavní sestavení nebo konkrétních prostředků satelitních sestavení. Hlavní sestavení a satelitní sestavení rozhraní .NET Framework poskytuje podporu pro správu verzí.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Atribut poskytuje podporu správy verzí pro hlavní sestavení. Zadání tohoto atributu na hlavní sestavení vaší aplikace můžete aktualizace a opětovné nasazení do hlavního sestavení bez aktualizace jeho satelitních sestavení. Po aktualizaci hlavní sestavení zvýšit číslo verze sestavení hlavní ale ponechejte číslo verze satelitního kontraktu beze změny. Pokud správce prostředků načte požadované prostředky, načte verzi satelitního sestavení určeném tento atribut.  
  
 Sestavení zásad vydavatele poskytovat podporu pro správu verzí satelitních sestavení. Můžete aktualizovat a znovu nasadit do satelitního sestavení bez aktualizace hlavní sestavení. Po aktualizaci satelitní sestavení zvýšit číslo verze a dodávat s sestavení zásad vydavatele. V sestavení zásad vydavatele, určit, že vaše nové satelitní sestavení zpětně kompatibilní s předchozí verzí. Správce prostředků bude používat <xref:System.Resources.SatelliteContractVersionAttribute> atribut k určení verze satelitního sestavení, ale zavaděč sestavení vytvoří vazbu k verzi satelitního sestavení určeném zásad vydavatele. Další informace o sestavení zásad vydavatele, naleznete v tématu [vytváření souboru zásad vydavatele](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Pokud chcete povolit podporu správy verzí úplná sestavení, doporučujeme vám, že nasadíte sestavení se silným názvem v [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md) a nasadit sestavení, které nemají silné názvy v adresáři aplikace. Pokud chcete nasadit sestavení se silným názvem v adresáři aplikace, nebude možné zvýšit číslo verze satelitního sestavení při aktualizaci sestavení. Místo toho je nutné provést aktualizaci na místě ve kterém nahraďte stávající kód s aktualizovaným kódem a udržovat stejné číslo verze. Například, pokud chcete aktualizovat verzi 1.0.0.0 satelitní sestavení s plně určený název sestavení "myApp.resources, verze 1.0.0.0, Culture = = de, PublicKeyToken = b03f5f11d50a3a", přepsat aktualizované myApp.resources.dll, který byl zkompilovaná sestavení stejné, plně zadaný název "myApp.resources, verze 1.0.0.0, jazyková verze = de, PublicKeyToken = = b03f5f11d50a3a". Všimněte si, že pomocí místní aktualizace pro soubory satelitního sestavení je těžké aplikaci, kterou přesně určit verzi satelitního sestavení.  
  
 Další informace o správě verzí sestavení naleznete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md) a [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>Načítání prostředků ze souborů .resources  
 Pokud se rozhodnete nasazení prostředků v satelitních sestaveních, které můžete použít <xref:System.Resources.ResourceManager> objektu pro přístup k prostředkům z .resources soubory přímo. Chcete-li to provést, musíte nasadit soubory .resources správně. Použít <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metoda pro vytvoření instance <xref:System.Resources.ResourceManager> objektu a zadejte adresář, který obsahuje samostatné soubory .resources.  
  
### <a name="deploying-resources-files"></a>Nasazení souborů .resources  
 Při vložení souborů .resources v sestavení aplikace a satelitní sestavení každé satelitní sestavení má stejný název souboru, ale je umístěn v podadresáři, která zohledňuje jazykovou verzi satelitního sestavení. Naproti tomu při přístupu k prostředkům ze souborů .resources přímo, můžete umístit všechny soubory .resources v jednom adresáři, obvykle jedná o podadresář adresáře aplikace. Název souboru .resources výchozí aplikace se skládá z názvu kořenového pouze, bez upozornění jeho jazykové verze (například strings.resources). Prostředky pro každou lokalizovanou jazykovou verzi jsou uloženy v souboru, jehož název se skládá z názvu kořenové a potom podle jazykové verze (například strings.ja.resources nebo strings.de-DE.resources). Následující ilustrace ukazuje, kde se soubory prostředků musí nacházet v adresářové struktuře.  
  
 ![Hlavní adresář pro vaši aplikaci](../../../docs/framework/resources/media/resappdir.gif "resappdir")  
Struktura adresářů a konvence pojmenování pro soubory .resources  
  
### <a name="using-the-resource-manager"></a>Pomocí Resource Manageru  
 Poté, co jste vytvořili prostředky a umístí je do příslušného adresáře, vytváření <xref:System.Resources.ResourceManager> objektu, který chcete používat prostředky voláním <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metody. První parametr určuje název kořenového souboru .resources výchozí aplikace (jde "řetězce", například v předchozí části). Druhý parametr určuje umístění prostředků ("Resources" předchozího příkladu). Třetí parametr určuje, <xref:System.Resources.ResourceSet> implementace. Pokud třetí parametr je `null`, výchozí modul runtime <xref:System.Resources.ResourceSet> se používá.  
  
> [!NOTE]
>  Nenasazujte aplikace pro ASP.NET pomocí samostatné soubory .resources. To může způsobit zamykání problémy a zalomení nasazení XCOPY. Doporučujeme nasadit prostředky technologie ASP.NET v satelitním sestavení. Další informace najdete v tématu [webové stránky ASP.NET: Přehled prostředků](https://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd).  
  
 Jakmile vytvoříte instanci <xref:System.Resources.ResourceManager> objektu, je použít <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, a <xref:System.Resources.ResourceManager.GetStream%2A> metod, jak je popsáno dříve k načtení prostředků. Načítání prostředků přímo ze souborů .resources se však liší od načtení vložených prostředků v sestavení. Při načtení prostředků ze souborů .resources <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody vždy načíst výchozí jazykové prostředky bez ohledu na aktuální jazykové verze. Chcete-li načíst prostředky buď aplikaci pro aktuální jazykovou verzi nebo konkrétní jazykové verze, musíte volat <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, nebo <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metoda a zadat jazykovou verzi, jehož prostředky se mají načíst. K načtení prostředků aktuální jazykové verze, zadejte hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost jako `culture` argument. Pokud správce prostředků nelze načíst z prostředků `culture`, používá záložní pravidla standardních prostředků k načtení příslušných prostředků.  
  
### <a name="an-example"></a>Příklad  
 Následující příklad ukazuje, jak správce prostředků načte prostředky přímo ze souborů .resources. Příklad se skládá ze tří souborů založený na textu prostředků pro angličtinu (Spojené státy), francouzština (Francie) a jazykové verze ruština (Rusko). Angličtina (Spojené státy) je v příkladu výchozí jazykovou verzi. Její prostředky jsou uložené v následujícím souboru s názvem Strings.txt:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Prostředky pro jazykovou verzi francouzština (Francie) jsou uloženy v následujícím souboru, který se nazývá Strings.fr-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Prostředky pro jazykovou verzi ruština (Rusko) jsou uloženy v následujícím souboru, který se nazývá Strings.ru-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Následující je zdrojový kód pro příklad. Příkladu je vytvořena instance <xref:System.Globalization.CultureInfo> objekty pro angličtinu (Spojené státy), angličtina (Kanada), francouzština (Francie) a jazykové verze ruština (Rusko) a provádí každý aktuální jazykové verze. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Metoda pak poskytuje hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost jako `culture` argument k načtení příslušné prostředky specifické pro jazykovou verzi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Verze jazyka C# v příkladu můžete zkompilovat spuštěním následující dávkového souboru. Pokud používáte jazyk Visual Basic, nahraďte `csc` s `vbc`a nahraďte `.cs` rozšíření s `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Resources.ResourceManager>  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Vytváření a načítání prostředků v aplikacích pro Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674)
