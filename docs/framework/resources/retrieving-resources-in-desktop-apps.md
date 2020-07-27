---
title: Načítání prostředků v aplikacích klasické pracovní plochy
description: Načtěte prostředky v desktopových aplikacích. Probalí prostředky pro výchozí (neutrální) jazykovou verzi s hlavním sestavením a vytvoří satelitní sestavení pro každou jazykovou verzi.
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
ms.openlocfilehash: db1156106690f8321b7fd5a2890c2aa44cfe17e3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166201"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Načítání prostředků v aplikacích klasické pracovní plochy

Při práci s lokalizovanými prostředky v .NET Framework desktopové aplikace byste měli ideálním balíčkem zabalit prostředky pro výchozí nebo neutrální jazykovou verzi pomocí hlavního sestavení a vytvořit samostatné satelitní sestavení pro každý jazyk nebo jazykovou verzi, kterou vaše aplikace podporuje. Pak můžete použít <xref:System.Resources.ResourceManager> třídu, jak je popsáno v další části, pro přístup k pojmenovaným prostředkům. Pokud se rozhodnete Nevkládat prostředky do hlavního sestavení a satelitních sestavení, můžete také přistupovat k binárním souborům. Resources přímo, jak je popsáno v části [načtení prostředků ze souborů. Resources](#from_file) dále v tomto článku.  Pokud chcete načíst prostředky v aplikacích pro Store ve Windows 8. x, přečtěte si téma [Vytvoření a načtení prostředků v aplikacích pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140)).  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Načítání prostředků ze sestavení  
 <xref:System.Resources.ResourceManager>Třída poskytuje přístup k prostředkům v době běhu. Použijte <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metodu pro načtení prostředků řetězce a <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> metody nebo pro načtení prostředků, které nejsou typu String. Každá metoda má dvě přetížení:  
  
- Přetížení, jehož jedním parametrem je řetězec, který obsahuje název prostředku. Metoda se pokusí načíst tento prostředek pro aktuální jazykovou verzi vlákna. Další informace naleznete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%29> metody, <xref:System.Resources.ResourceManager.GetObject%28System.String%29> a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> .  
  
- Přetížení, které má dva parametry: řetězec obsahující název prostředku a <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, jejíž prostředek má být načten. Pokud se sada prostředků pro tuto jazykovou verzi nenajde, správce prostředků použije náhradní pravidla k načtení příslušného prostředku. Další informace naleznete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29> metody, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29> a <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> .  
  
 Správce prostředků používá proces pro použití náhradních prostředků k řízení toho, jak aplikace načítá prostředky specifické pro jazykovou verzi. Další informace najdete v části "proces záložního prostředku" v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md). Informace o vytváření instancí <xref:System.Resources.ResourceManager> objektu naleznete v části "vytvoření objektu Správce prostředků" v <xref:System.Resources.ResourceManager> tématu třídy.  
  
### <a name="retrieving-string-data-an-example"></a>Načítají se data řetězce: příklad  
 Následující příklad volá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodu pro načtení prostředků řetězce aktuální jazykové verze uživatelského rozhraní. Zahrnuje prostředek neutrálního řetězce pro anglickou (USA) jazykovou verzi a lokalizované prostředky pro jazykové verze francouzština (Francie) a ruština (Rusko). Následující prostředek v angličtině (USA) je v souboru s názvem Strings.txt:  
  
```text
TimeHeader=The current time is  
```  
  
 Zdroj francouzština (Francie) je v souboru s názvem Strings.fr-FR.txt:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Prostředek ruštiny (Rusko) je v souboru s názvem Strings.ru-RU-txt:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Zdrojový kód pro tento příklad, který je v souboru s názvem GetString.cs pro verzi jazyka C# kódu a GetString. vb pro Visual Basic verze, definuje pole řetězců, které obsahuje název čtyř kultur: tři jazykové verze, pro které jsou k dispozici prostředky a španělština (Španělsko) culture. Smyčka, která provede pět časů náhodně vybere jednu z těchto jazykových verzí a přiřadí ji k <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnostem a. Poté volá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodu pro načtení lokalizovaného řetězce, který se zobrazí spolu s denním časem.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Následující soubor dávky (. bat) zkompiluje příklad a generuje satelitní sestavení v příslušných adresářích. Příkazy jsou k dispozici pro jazyk a kompilátor jazyka C#. Pro Visual Basic, změňte `csc` na `vbc` a změňte `GetString.cs` na `GetString.vb` .  
  
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
  
 Pokud je aktuální jazyková verze uživatelského rozhraní španělština (Španělsko), Všimněte si, že v příkladu se zobrazí prostředky anglické jazykové verze, protože španělské jazykové prostředky nejsou k dispozici a angličtina je výchozí jazyková verze příkladu.  
  
### <a name="retrieving-object-data-two-examples"></a>Načítání dat objektu: dva příklady  
 <xref:System.Resources.ResourceManager.GetObject%2A> <xref:System.Resources.ResourceManager.GetStream%2A> K načtení dat objektu lze použít metody a. To zahrnuje primitivní datové typy, serializovatelné objekty a objekty, které jsou uloženy v binárním formátu (například obrázky).  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metodu k načtení rastrového obrázku, který se používá v úvodním okně aplikace. Následující zdrojový kód v souboru s názvem CreateResources.cs (pro C#) nebo CreateResources. vb (pro Visual Basic) vygeneruje soubor. resx, který obsahuje serializovanou bitovou kopii. V takovém případě je bitová kopie načtena ze souboru s názvem SplashScreen.jpg; název souboru můžete změnit tak, aby nahradil vlastní image.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Následující kód načte prostředek a zobrazí obrázek v <xref:System.Windows.Forms.PictureBox> ovládacím prvku.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Příklad jazyka C# můžete vytvořit pomocí následujícího dávkového souboru. Pro Visual Basic, změňte `csc` na `vbc` a změňte rozšíření souboru zdrojového kódu z `.cs` na `.vb` .  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodu k deserializaci vlastního objektu. Příklad obsahuje soubor zdrojového kódu s názvem UIElements.cs (UIElement. vb pro Visual Basic), který definuje následující strukturu s názvem `PersonTable` . Tato struktura je určena pro použití v obecné rutině zobrazení tabulky, která zobrazuje lokalizované názvy sloupců tabulky. Všimněte si, že `PersonTable` struktura je označena <xref:System.SerializableAttribute> atributem.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Následující kód ze souboru s názvem CreateResources.cs (CreateResources. vb pro Visual Basic) vytvoří soubor prostředků XML s názvem UIResources. resx, který ukládá název tabulky a objekt obsahující `PersonTable` informace pro aplikaci, která je lokalizována do anglického jazyka.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Následující kód v souboru zdrojového kódu s názvem GetObject.cs (GetObject. vb) následně načte prostředky a zobrazí je v konzole nástroje.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Můžete sestavit potřebný soubor prostředků a sestavení a spustit aplikaci spuštěním následujícího dávkového souboru. K `/r` poskytnutí Resgen.exe s odkazem na UIElements.dll je nutné použít možnost, aby bylo možné získat přístup k informacím o `PersonTable` struktuře. Pokud používáte jazyk C#, nahraďte `vbc` název kompilátoru názvem `csc` a nahraďte příponu parametrem `.vb` `.cs` .  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Podpora správy verzí pro satelitní sestavení  
 Ve výchozím nastavení, když <xref:System.Resources.ResourceManager> objekt načte požadované prostředky, vyhledá satelitní sestavení s čísly verze, která odpovídají číslu verze hlavního sestavení. Po nasazení aplikace je vhodné aktualizovat hlavní sestavení nebo konkrétní satelitní sestavení prostředků. .NET Framework poskytuje podporu pro správu verzí hlavního sestavení a satelitních sestavení.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute>Atribut poskytuje podporu správy verzí pro hlavní sestavení. Zadání tohoto atributu pro hlavní sestavení aplikace umožňuje aktualizovat a znovu nasadit hlavní sestavení bez aktualizace jeho satelitních sestavení. Po aktualizaci hlavního sestavení Zvyšte číslo verze hlavního sestavení, ale ponechte číslo verze satelitního kontraktu beze změny. Když správce prostředků načte požadované prostředky, načte verzi satelitního sestavení určenou tímto atributem.  
  
 Sestavení zásad vydavatele poskytují podporu pro satelitní sestavení se správou verzí. Satelitní sestavení můžete aktualizovat a znovu nasadit bez aktualizace hlavního sestavení. Po aktualizaci satelitního sestavení zvyšte jeho číslo verze a odešlete ho do sestavení zásad vydavatele. V sestavení zásad vydavatele určete, že nové satelitní sestavení je zpětně kompatibilní s předchozí verzí. Správce prostředků použije <xref:System.Resources.SatelliteContractVersionAttribute> atribut k určení verze satelitního sestavení, ale zavaděč sestavení vytvoří vazby na verzi satelitního sestavení určenou v zásadě vydavatele. Další informace o sestaveních zásad vydavatele najdete v tématu [Vytvoření souboru zásad vydavatele](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Chcete-li povolit podporu plné verze sestavení, doporučujeme nasadit sestavení se silným názvem do [globální mezipaměti sestavení (GAC](../app-domains/gac.md) ) a nasadit sestavení, která nemají silné názvy v adresáři aplikace. Pokud chcete nasadit sestavení se silným názvem v adresáři aplikace, nebudete moci zvýšit číslo verze satelitního sestavení při aktualizaci sestavení. Místo toho je nutné provést místní aktualizaci, kde nahradíte stávající kód aktualizovaným kódem a zachováte stejné číslo verze. Například pokud chcete aktualizovat verzi 1.0.0.0 satelitního sestavení s plně určeným názvem sestavení "myApp. Resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a", přepište ji pomocí aktualizované myApp.resources.dll, která byla zkompilována se stejným plně zadaným názvem sestavení "myApp. Resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a". Všimněte si, že použití místních aktualizací u satelitních souborů sestavení ztěžuje aplikaci přesné určení verze satelitního sestavení.  
  
 Další informace o tom, jak sestavovat verze sestavení, najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md) a [způsob, jakým modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>Načítání prostředků ze souborů. Resources  
 Pokud se rozhodnete nenasadit prostředky v satelitních sestaveních, můžete i nadále použít <xref:System.Resources.ResourceManager> objekt pro přístup k prostředkům ze souborů. Resources přímo. K tomu je nutné nasadit soubory. Resources správně. Pak použijte <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metodu pro vytvoření instance <xref:System.Resources.ResourceManager> objektu a určení adresáře, který obsahuje soubory Standalone. Resources.  
  
### <a name="deploying-resources-files"></a>Nasazení souborů. Resources  
 Při vkládání souborů. Resources v sestavení aplikace a satelitních sestaveních má každé satelitní sestavení stejný název souboru, ale je umístěn v podadresáři, který odráží jazykovou verzi satelitního sestavení. Naopak když přistupujete k prostředkům ze souborů. Resources přímo, můžete umístit všechny soubory. Resources do jednoho adresáře, obvykle do podadresáře adresáře aplikace. Název souboru Default. Resources aplikace se skládá pouze z kořenového názvu, bez označení jeho jazykové verze (například Strings. Resources). Prostředky pro každou lokalizovanou jazykovou verzi jsou uloženy v souboru, jehož název se skládá z kořenového názvu následovaného jazykovou verzí (například Strings. ja. Resources nebo strings.de-DE. Resources).

 Následující obrázek ukazuje, kde by se měly soubory prostředků umístit do adresářové struktury. Poskytuje také zásady vytváření názvů pro soubory prostředků.  

 ![Ilustrace znázorňující hlavní adresář pro vaši aplikaci.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Použití Správce prostředků  
 Po vytvoření prostředků a jejich umístění do příslušného adresáře vytvoříte <xref:System.Resources.ResourceManager> objekt pro použití prostředků voláním <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metody. První parametr určuje kořenový název souboru Default. Resources aplikace (to by bylo "řetězce" pro příklad v předchozí části). Druhý parametr určuje umístění prostředků ("prostředky" pro předchozí příklad). Třetí parametr určuje implementaci, <xref:System.Resources.ResourceSet> která se má použít. Pokud je třetí parametr `null` , je použit výchozí modul runtime <xref:System.Resources.ResourceSet> .  
  
> [!NOTE]
> Nesaďte aplikace ASP.NET pomocí samostatných souborů. Resources. To může způsobit problémy s uzamčením a přerušením nasazení XCOPY. Doporučujeme, abyste nasadili prostředky ASP.NET v satelitních sestaveních. Další informace najdete v tématu [Přehled prostředků webové stránky ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po vytvoření instance <xref:System.Resources.ResourceManager> objektu použijte <xref:System.Resources.ResourceManager.GetString%2A> metody, a, jak je <xref:System.Resources.ResourceManager.GetObject%2A> <xref:System.Resources.ResourceManager.GetStream%2A> popsáno výše, k načtení prostředků. Načítání prostředků přímo ze souborů. Resources se ale liší od načtení integrovaných prostředků ze sestavení. Když načtete prostředky ze souborů. Resources <xref:System.Resources.ResourceManager.GetString%28System.String%29> , <xref:System.Resources.ResourceManager.GetObject%28System.String%29> metody, a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> vždy načtou prostředky výchozí jazykové verze bez ohledu na aktuální jazykovou verzi. Chcete-li načíst prostředky z aktuální jazykové verze aplikace nebo konkrétní jazykové verze, je nutné zavolat <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29> <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29> metodu, nebo <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> a zadat jazykovou verzi, jejíž prostředky mají být načteny. Chcete-li načíst prostředky aktuální jazykové verze, zadejte hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti jako `culture` argument. Pokud správce prostředků nemůže získat prostředky `culture` , používá standardní záložní pravidla prostředků k načtení příslušných prostředků.  
  
### <a name="an-example"></a>Příklad  
 Následující příklad ukazuje, jak správce prostředků získává prostředky přímo ze souborů. Resources. Příklad obsahuje tři textové soubory prostředků pro anglickou (USA), francouzština (Francie) a ruštinu (Rusko) kultur. Angličtina (USA) je výchozí jazyková verze příkladu. Jeho prostředky jsou uloženy v následujícím souboru s názvem Strings.txt:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Prostředky pro francouzskou (Francii) jazykovou verzi jsou uloženy v následujícím souboru s názvem Strings.fr-FR.txt:  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Prostředky pro jazykovou verzi ruštiny (Rusko) jsou uloženy v následujícím souboru s názvem Strings.ru-RU.txt:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Následuje zdrojový kód pro příklad. Příklad vytvoří instanci <xref:System.Globalization.CultureInfo> objektů pro angličtinu (USA), angličtinu (Kanada), francouzština (Francie) a ruština (Rusko) a zpřístupňuje každou aktuální jazykovou verzi. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>Metoda pak dodá hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti jako `culture` argument pro načtení příslušných prostředků specifických pro jazykovou verzi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Verzi v C# příkladu můžete zkompilovat spuštěním následujícího dávkového souboru. Pokud používáte Visual Basic, nahraďte `csc` `vbc` a nahraďte příponu parametrem `.cs` `.vb` .  
  
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
