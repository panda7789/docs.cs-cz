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
ms.openlocfilehash: 3c14e251b6ca88fb864952c3411b5ea0c46da302
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129942"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Načítání prostředků v aplikacích klasické pracovní plochy
Při práci s lokalizovanými prostředky v .NET Framework desktopové aplikace byste měli ideálním balíčkem zabalit prostředky pro výchozí nebo neutrální jazykovou verzi pomocí hlavního sestavení a vytvořit samostatné satelitní sestavení pro každý jazyk nebo jazykovou verzi, kterou vaše aplikace podporuje. Pak můžete použít třídu <xref:System.Resources.ResourceManager>, jak je popsáno v další části, pro přístup k pojmenovaným prostředkům. Pokud se rozhodnete Nevkládat prostředky do hlavního sestavení a satelitních sestavení, můžete také přistupovat k binárním souborům. Resources přímo, jak je popsáno v části [načtení prostředků ze souborů. Resources](#from_file) dále v tomto článku.  Pokud chcete načíst prostředky v aplikacích [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], přečtěte si téma [Vytvoření a načtení prostředků v aplikacích pro Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674) na stránce Windows Dev Center.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Načítání prostředků ze sestavení  
 Třída <xref:System.Resources.ResourceManager> poskytuje přístup k prostředkům v době běhu. Použijte metodu <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> k načtení prostředků řetězce a metody <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> nebo <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> pro načtení prostředků, které nejsou řetězcem. Každá metoda má dvě přetížení:  
  
- Přetížení, jehož jedním parametrem je řetězec, který obsahuje název prostředku. Metoda se pokusí načíst tento prostředek pro aktuální jazykovou verzi vlákna. Další informace najdete v metodách <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>a <xref:System.Resources.ResourceManager.GetStream%28System.String%29>.  
  
- Přetížení, které má dva parametry: řetězec obsahující název prostředku a objekt <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi, jejíž prostředek má být načten. Pokud se sada prostředků pro tuto jazykovou verzi nenajde, správce prostředků použije náhradní pravidla k načtení příslušného prostředku. Další informace najdete v metodách <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>a <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29>.  
  
 Správce prostředků používá proces pro použití náhradních prostředků k řízení toho, jak aplikace načítá prostředky specifické pro jazykovou verzi. Další informace najdete v části "proces záložního prostředku" v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md). Informace o vytváření instancí objektu <xref:System.Resources.ResourceManager> naleznete v části "vytvoření objektu ResourceManager" v tématu <xref:System.Resources.ResourceManager> třídy.  
  
### <a name="retrieving-string-data-an-example"></a>Načítají se data řetězce: příklad  
 Následující příklad volá metodu <xref:System.Resources.ResourceManager.GetString%28System.String%29> pro načtení prostředků řetězce aktuální jazykové verze uživatelského rozhraní. Zahrnuje prostředek neutrálního řetězce pro anglickou (USA) jazykovou verzi a lokalizované prostředky pro jazykové verze francouzština (Francie) a ruština (Rusko). Následující prostředek v angličtině (USA) je v souboru s názvem Strings. txt:  
  
```text
TimeHeader=The current time is  
```  
  
 Zdroj francouzština (Francie) je v souboru s názvem Strings.fr-FR. txt:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Prostředek ruštiny (Rusko) je v souboru s názvem Strings.ru-RU-txt:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Zdrojový kód pro tento příklad, který je v souboru s názvem GetString.cs pro C# verzi kódu a GetString. vb pro Visual Basic verzi, definuje pole řetězců, které obsahuje název čtyř kultur: tři jazykové verze, pro které jsou prostředky dostupné a španělská jazyková verze (Španělsko). Smyčka, která provede pět časů náhodně vybere jednu z těchto jazykových verzí a přiřadí ji k vlastnostem <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>. Poté volá metodu <xref:System.Resources.ResourceManager.GetString%28System.String%29> pro načtení lokalizovaného řetězce, který se zobrazí spolu s denním časem.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Následující soubor dávky (. bat) zkompiluje příklad a generuje satelitní sestavení v příslušných adresářích. Příkazy jsou k dispozici pro C# jazyk a kompilátor. V případě Visual Basic změňte `csc` na `vbc`a změňte `GetString.cs` na `GetString.vb`.  
  
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
 K načtení dat objektu lze použít metody <xref:System.Resources.ResourceManager.GetObject%2A> a <xref:System.Resources.ResourceManager.GetStream%2A>. To zahrnuje primitivní datové typy, serializovatelné objekty a objekty, které jsou uloženy v binárním formátu (například obrázky).  
  
 Následující příklad používá metodu <xref:System.Resources.ResourceManager.GetStream%28System.String%29> k načtení rastrového obrázku, který se používá v úvodním okně aplikace. Následující zdrojový kód v souboru s názvem CreateResources.cs (for C#) nebo CreateResources. vb (pro Visual Basic) vygeneruje soubor. resx, který obsahuje serializovanou bitovou kopii. V tomto případě je bitová kopie načtena ze souboru s názvem třídy SplashScreen. jpg; název souboru můžete změnit tak, aby nahradil vlastní image.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Následující kód načte prostředek a zobrazí obrázek v ovládacím prvku <xref:System.Windows.Forms.PictureBox>.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Pomocí následujícího dávkového souboru můžete C# příklad sestavit. Pro Visual Basic změňte `csc` na `vbc`a změňte rozšíření souboru zdrojového kódu z `.cs` na `.vb`.  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Následující příklad používá metodu <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> k deserializaci vlastního objektu. Příklad obsahuje soubor zdrojového kódu s názvem UIElements.cs (UIElement. vb pro Visual Basic), který definuje následující strukturu s názvem `PersonTable`. Tato struktura je určena pro použití v obecné rutině zobrazení tabulky, která zobrazuje lokalizované názvy sloupců tabulky. Všimněte si, že struktura `PersonTable` je označena atributem <xref:System.SerializableAttribute>.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Následující kód ze souboru s názvem CreateResources.cs (CreateResources. vb pro Visual Basic) vytvoří soubor prostředků XML s názvem UIResources. resx, který ukládá název tabulky a `PersonTable` objekt, který obsahuje informace pro aplikaci, která je lokalizována pro Anglický jazyk.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Následující kód v souboru zdrojového kódu s názvem GetObject.cs (GetObject. vb) následně načte prostředky a zobrazí je v konzole nástroje.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Můžete sestavit potřebný soubor prostředků a sestavení a spustit aplikaci spuštěním následujícího dávkového souboru. Je nutné použít možnost `/r` k poskytnutí nástroje Resgen. exe s odkazem na prvek UIElement. dll, aby měl přístup k informacím o `PersonTable` struktuře. Pokud používáte C#, nahraďte název `vbc` kompilátoru pomocí `csc`a nahraďte příponu `.vb` `.cs`.  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Podpora správy verzí pro satelitní sestavení  
 Ve výchozím nastavení, když objekt <xref:System.Resources.ResourceManager> načte požadované prostředky, vyhledá satelitní sestavení s čísly verze, která odpovídají číslu verze hlavního sestavení. Po nasazení aplikace je vhodné aktualizovat hlavní sestavení nebo konkrétní satelitní sestavení prostředků. .NET Framework poskytuje podporu pro správu verzí hlavního sestavení a satelitních sestavení.  
  
 Atribut <xref:System.Resources.SatelliteContractVersionAttribute> poskytuje podporu správy verzí pro hlavní sestavení. Zadání tohoto atributu pro hlavní sestavení aplikace umožňuje aktualizovat a znovu nasadit hlavní sestavení bez aktualizace jeho satelitních sestavení. Po aktualizaci hlavního sestavení Zvyšte číslo verze hlavního sestavení, ale ponechte číslo verze satelitního kontraktu beze změny. Když správce prostředků načte požadované prostředky, načte verzi satelitního sestavení určenou tímto atributem.  
  
 Sestavení zásad vydavatele poskytují podporu pro satelitní sestavení se správou verzí. Satelitní sestavení můžete aktualizovat a znovu nasadit bez aktualizace hlavního sestavení. Po aktualizaci satelitního sestavení zvyšte jeho číslo verze a odešlete ho do sestavení zásad vydavatele. V sestavení zásad vydavatele určete, že nové satelitní sestavení je zpětně kompatibilní s předchozí verzí. Správce prostředků použije atribut <xref:System.Resources.SatelliteContractVersionAttribute> k určení verze satelitního sestavení, ale zavaděč sestavení vytvoří vazby na verzi satelitního sestavení určenou v zásadě vydavatele. Další informace o sestaveních zásad vydavatele najdete v tématu [Vytvoření souboru zásad vydavatele](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Chcete-li povolit podporu plné verze sestavení, doporučujeme nasadit sestavení se silným názvem do [globální mezipaměti sestavení (GAC](../app-domains/gac.md) ) a nasadit sestavení, která nemají silné názvy v adresáři aplikace. Pokud chcete nasadit sestavení se silným názvem v adresáři aplikace, nebudete moci zvýšit číslo verze satelitního sestavení při aktualizaci sestavení. Místo toho je nutné provést místní aktualizaci, kde nahradíte stávající kód aktualizovaným kódem a zachováte stejné číslo verze. Například pokud chcete aktualizovat verzi 1.0.0.0 satelitního sestavení s plně určeným názvem sestavení "myApp. Resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a", přepište ji pomocí aktualizovaného myApp. Resources. dll, který byl kompilováno se stejným plně zadaným názvem sestavení "myApp. Resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a". Všimněte si, že použití místních aktualizací u satelitních souborů sestavení ztěžuje aplikaci přesné určení verze satelitního sestavení.  
  
 Další informace o tom, jak sestavovat verze sestavení, najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md) a [způsob, jakým modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>Načítání prostředků ze souborů. Resources  
 Pokud se rozhodnete nenasadit prostředky v satelitních sestaveních, můžete i nadále použít objekt <xref:System.Resources.ResourceManager> pro přístup k prostředkům ze souborů. Resources přímo. K tomu je nutné nasadit soubory. Resources správně. Pak použijte metodu <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> pro vytvoření instance objektu <xref:System.Resources.ResourceManager> a určete adresář, který obsahuje soubory Standalone. Resources.  
  
### <a name="deploying-resources-files"></a>Nasazení souborů. Resources  
 Při vkládání souborů. Resources v sestavení aplikace a satelitních sestaveních má každé satelitní sestavení stejný název souboru, ale je umístěn v podadresáři, který odráží jazykovou verzi satelitního sestavení. Naopak když přistupujete k prostředkům ze souborů. Resources přímo, můžete umístit všechny soubory. Resources do jednoho adresáře, obvykle do podadresáře adresáře aplikace. Název souboru Default. Resources aplikace se skládá pouze z kořenového názvu, bez označení jeho jazykové verze (například Strings. Resources). Prostředky pro každou lokalizovanou jazykovou verzi jsou uloženy v souboru, jehož název se skládá z kořenového názvu následovaného jazykovou verzí (například Strings. ja. Resources nebo strings.de-DE. Resources). 
 
 Následující obrázek ukazuje, kde by se měly soubory prostředků umístit do adresářové struktury. Poskytuje také zásady vytváření názvů pro soubory prostředků.  

 ![Ilustrace znázorňující hlavní adresář pro vaši aplikaci.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Použití Správce prostředků  
 Po vytvoření prostředků a jejich umístění do příslušného adresáře vytvoříte objekt <xref:System.Resources.ResourceManager> pro použití prostředků voláním metody <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29>. První parametr určuje kořenový název souboru Default. Resources aplikace (to by bylo "řetězce" pro příklad v předchozí části). Druhý parametr určuje umístění prostředků ("prostředky" pro předchozí příklad). Třetí parametr určuje <xref:System.Resources.ResourceSet> implementaci, která se má použít. Pokud je třetí parametr `null`, použije se výchozí modul runtime <xref:System.Resources.ResourceSet>.  
  
> [!NOTE]
> Nesaďte aplikace ASP.NET pomocí samostatných souborů. Resources. To může způsobit problémy s uzamčením a přerušením nasazení XCOPY. Doporučujeme, abyste nasadili prostředky ASP.NET v satelitních sestaveních. Další informace najdete v tématu [Přehled prostředků webové stránky ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po vytvoření instance objektu <xref:System.Resources.ResourceManager> použijte metody <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>a <xref:System.Resources.ResourceManager.GetStream%2A>, jak je popsáno výše, k načtení prostředků. Načítání prostředků přímo ze souborů. Resources se ale liší od načtení integrovaných prostředků ze sestavení. Když načtete prostředky ze souborů. Resources, metody <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> vždy načtou prostředky výchozí jazykové verze bez ohledu na aktuální jazykovou verzi. Chcete-li načíst prostředky z aktuální jazykové verze aplikace nebo konkrétní jazykové verze, je nutné volat metodu <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>nebo <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> a zadat jazykovou verzi, jejíž prostředky mají být načteny. Chcete-li načíst prostředky aktuální jazykové verze, zadejte hodnotu vlastnosti <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jako argument `culture`. Pokud správce prostředků nemůže načíst prostředky `culture`, používá ke získání odpovídajících prostředků standardní pravidla pro použití náhradního prostředku.  
  
### <a name="an-example"></a>Příklad  
 Následující příklad ukazuje, jak správce prostředků získává prostředky přímo ze souborů. Resources. Příklad obsahuje tři textové soubory prostředků pro anglickou (USA), francouzština (Francie) a ruštinu (Rusko) kultur. Angličtina (USA) je výchozí jazyková verze příkladu. Jeho prostředky jsou uloženy v následujícím souboru s názvem Strings. txt:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Prostředky pro francouzskou (Francii) jazykovou verzi jsou uloženy v následujícím souboru s názvem Strings.fr-FR. txt:  
  
```text 
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Prostředky pro jazykovou verzi ruštiny (Rusko) jsou uloženy v následujícím souboru s názvem Strings.ru-RU. txt:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Následuje zdrojový kód pro příklad. Příklad vytvoří instanci <xref:System.Globalization.CultureInfo> objektů pro angličtinu (USA), angličtinu (Kanada), francouzštinu (Francie) a ruštinu (Rusko) a zpřístupňuje každou aktuální jazykovou verzi. Metoda <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> pak poskytuje hodnotu vlastnosti <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jako argument `culture` pro načtení příslušných prostředků specifických pro jazykovou verzi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 C# Verzi příkladu můžete zkompilovat spuštěním následujícího dávkového souboru. Pokud používáte Visual Basic, nahraďte `csc` `vbc`a nahraďte `.cs` příponou `.vb`.  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Resources.ResourceManager>
- [Prostředky v desktopových aplikacích](index.md)
- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Vytváření a načítání prostředků v aplikacích pro Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674)
