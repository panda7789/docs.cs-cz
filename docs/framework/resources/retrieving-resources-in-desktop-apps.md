---
title: "Načítání prostředků v aplikacích klasické pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c1b751fc5fb5717ad4bf030777359bef2e69545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-resources-in-desktop-apps"></a>Načítání prostředků v aplikacích klasické pracovní plochy
Při práci s místní zdroje v aplikacích klasické pracovní plochy rozhraní .NET Framework by v ideálním případě prostředky pro výchozí nebo neutrální jazykovou verzi balíčku s hlavní sestavení a vytvořte samostatné satelitní sestavení pro každý jazyk nebo jazykovou verzi, která vaše aplikace podporuje. Pak můžete použít <xref:System.Resources.ResourceManager> třídy, jak je popsáno v následující části pro přístup k prostředkům s názvem. Pokud se rozhodnete, že není v hlavní sestavení a satelitní sestavení pro vložení vašich prostředků, můžete taky přejít binární soubory RESOURCES přímo, jak je popsáno v části [načítání prostředky z soubory .resources](#from_file) později v tomto článek.  Načtení prostředků v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v části [vytváření a načítání prostředků v aplikacích pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=241674) ve službě Windows Dev Center.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Načítání prostředků ze sestavení  
 <xref:System.Resources.ResourceManager> Třída poskytuje přístup k prostředkům v době běhu. Můžete použít <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metoda pro načtení řetězcové prostředky a <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> nebo <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> metoda pro načtení prostředků jiné než řetězec. Každá z metod má dvě přetížení:  
  
-   Přetížení jejichž jediný parametr je řetězec, který obsahuje název prostředku. Metoda se pokusí načíst prostředku pro aktuální jazykovou verzi vlákna. Další informace najdete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
-   Přetížení, které má dva parametry: řetězec, který obsahuje název prostředku a <xref:System.Globalization.CultureInfo> objekt, který reprezentuje jazykovou verzi, jejichž prostředek se má načíst. Pokud prostředek pro nastavené, že jazykovou verzi nelze najít, správce prostředků používá záložní pravidla načíst odpovídající prostředek. Další informace najdete v tématu <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Správce prostředků používá záložní proces prostředků k řízení způsobu, jakým aplikace načítat prostředky specifické pro jazykovou verzi. Další informace najdete v části "Proces nouzového prostředku" v [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Informace o vytváření instancí <xref:System.Resources.ResourceManager> objektu, najdete v části "Vytváření instancí ResourceManager objekt" v <xref:System.Resources.ResourceManager> třída tématu.  
  
### <a name="retrieving-string-data-an-example"></a>Načítání dat řetězců: Příklad  
 Následující příklad volání <xref:System.Resources.ResourceManager.GetString%28System.String%29> metoda pro načtení řetězcové prostředky aktuální jazykové verze uživatelského rozhraní. Francouzština (Francie) a kultur ruskými obsahuje neutrální řetězec prostředku pro jazykovou verzi Angličtina (Spojené státy) a lokalizované prostředky. V následujícím zdroji Czech (Czech Republic) je v souboru s názvem Strings.txt:  
  
```  
TimeHeader=The current time is  
```  
  
 Francouzština (Francie) prostředku je v souboru s názvem Strings.fr-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Prostředek ruskými je do souboru s názvem Strings.ru-RU-txt:  
  
```  
TimeHeader=Текущее время —  
```  
  
 Zdrojový kód pro tento příklad, který je v souboru s názvem GetString.cs pro C# verzi kódu a GetString.vb pro verzi jazyka Visual Basic, definuje pole řetězců obsahující název jazykové verze čtyři: tři jazykové verze, pro které jsou k dispozici prostředky a Španělština (Španělsko) jazykovou verzi. Smyčku, které provádí pětkrát náhodně vybere jeden z těchto jazykové verze a přiřadí ji k <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti. Potom zavolá <xref:System.Resources.ResourceManager.GetString%28System.String%29> metoda pro načtení lokalizované řetězce, který se zobrazí spolu s denní dobu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Následující soubor batch (.bat) kompiluje v příkladu a vygeneruje satelitní sestavení v adresáři odpovídající. Příkazy jsou uvedené pro jazyk C# a kompilátoru. V jazyce Visual Basic změnit `csc` k `vbc`a změňte `GetString.cs` k `GetString.vb`.  
  
```  
resgen strings.txt  
csc GetString.cs /resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al /embed:strings.fr-FR.resources /culture:fr-FR /out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al /embed:strings.ru-RU.resources /culture:ru-RU /out:ru-RU\GetString.resources.dll  
```  
  
 Pokud aktuální jazykové verze uživatelského rozhraní španělština (Španělsko), Všimněte si, že v příkladu se zobrazí anglickými prostředky, protože nejsou k dispozici prostředky španělštiny a výchozí jazykovou verzi v příkladu je angličtina.  
  
### <a name="retrieving-object-data-two-examples"></a>Načítání dat objektu: Dva příklady  
 Můžete použít <xref:System.Resources.ResourceManager.GetObject%2A> a <xref:System.Resources.ResourceManager.GetStream%2A> metody k načtení dat objektu. To zahrnuje primitivní datové typy, serializovatelné objekty a objekty, které jsou uloženy v binárním formátu (například obrázky).  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metoda pro načtení rastrového obrázku, který se používá v aplikaci je otevřete úvodní okno. Následující zdrojový kód v souboru s názvem CreateResources.cs (pro jazyk C#) nebo CreateResources.vb (pro Visual Basic) generuje soubor .resx, který obsahuje bitovou kopii serializovaných. V takovém případě je se obrázek načetl ze souboru s názvem SplashScreen.jpg; můžete upravit název souboru k nahrazení vlastní image.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Následující kód načte prostředek a zobrazí obrázek <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Následující dávkový soubor můžete použít k vytvoření příklad jazyka C#. V jazyce Visual Basic změnit `csc` k `vbc`a změňte příponu souboru zdrojového kódu z `.cs` k `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs /resource:AppResources.resources  
```  
  
 Následující příklad používá <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodu pro deserializaci vlastních objektů. Příklad obsahuje zdrojový soubor s názvem UIElements.cs (UIElements.vb jazyka Visual Basic), která definuje následující strukturu s názvem `PersonTable`. Tato struktura je určena pro použití ve zobrazení rutinou obecná tabulka, která zobrazuje lokalizované názvy sloupců tabulky. Všimněte si, že `PersonTable` struktura je označené jako <xref:System.SerializableAttribute> atribut.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Následující kód do souboru s názvem CreateResources.cs (CreateResources.vb jazyka Visual Basic) vytvoří soubor XML prostředků s názvem UIResources.resx, která ukládá název tabulky a `PersonTable` objekt, který obsahuje informace o aplikaci, která je lokalizován do Anglickém jazyce.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Následující kód v souboru zdrojového kódu s názvem GetObject.cs (GetObject.vb) potom načte prostředky a zobrazí je ke konzole.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Můžete sestavit souboru nezbytné prostředků a sestavení a spuštění aplikace tak, že spustíte následující dávkového souboru. Je nutné použít `/r` možnost zadat Resgen.exe s odkazem na UIElements.dll tak, aby se přístup k informacím o `PersonTable` struktura. Pokud používáte C#, nahraďte `vbc` název kompilátoru s `csc`a nahraďte `.vb` rozšíření s `.cs`.  
  
```  
vbc /t:library UIElements.vb  
vbc CreateResources.vb /r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  /r:UIElements.dll  
vbc GetObject.vb /r:UIElements.dll /resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Podpora správy verzí pro satelitní sestavení  
 Ve výchozím nastavení když <xref:System.Resources.ResourceManager> objekt načítá požadované prostředky, hledá satelitní sestavení, které mají čísla verzí, která odpovídají číslo verze hlavního sestavení. Po nasazení aplikace, můžete chtít aktualizovat hlavní sestavení nebo prostředku satelitní sestavení. Hlavní sestavení a satelitních sestavení rozhraní .NET Framework poskytuje podporu pro správu verzí.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Atribut poskytuje podporu správy verzí pro hlavní sestavení. Zadání tohoto atributu na hlavní sestavení aplikace umožňuje aktualizovat a znovu nasaďte hlavní sestavení bez aktualizace jeho satelitních sestavení. Po aktualizaci hlavní sestavení, zvýšíte číslo verze hlavní sestavení, ale ponechte číslo verze smlouvy satelitní beze změny. Pokud správce prostředků načítá požadované prostředky, načte verze sestavení satelitní určeného tento atribut.  
  
 Sestavení zásady vydavatele poskytují podporu pro správu verzí satelitních sestavení. Můžete aktualizovat a znovu nasaďte satelitní sestavení bez aktualizace hlavní sestavení. Po aktualizaci satelitní sestavení, zvýšit jeho číslo verze a dodávat s sestavení zásady vydavatele. V sestavení zásady vydavatele určit, že nové satelitní sestavení je zpětně kompatibilní s jeho předchozí verze. Správce prostředků bude používat <xref:System.Resources.SatelliteContractVersionAttribute> atribut určení verze satelitní sestavení, ale zavaděč sestavení vytvoří vazbu k satelitní sestavení verze zadaná zásad vydavatele. Další informace o sestavení zásady vydavatele najdete v tématu [vytvoření souboru zásad vydavatele](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Pro podporu správy verzí úplné sestavení, doporučujeme, abyste nasadili sestavení se silným názvem v [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md) a nasadit sestavení, které nemají silné názvy v adresáři aplikace. Pokud chcete nasadit sestavení se silným názvem v adresáři aplikace, nebude možné zvýšit číslo verze sestavení satelitní při aktualizaci sestavení. Místo toho je nutné provést aktualizaci na místě, kde nahraďte kód aktualizované stávající kód a zachovat stejné číslo verze. Například, pokud chcete aktualizovat verzi 1.0.0.0 satelitní sestavení s názvem plně zadaného sestavení "myApp.resources, verzi 1.0.0.0, Culture = = de, PublicKeyToken = b03f5f11d50a3a", přepsat aktualizovanou knihovnou myApp.Resources.dll, která byla Kompilovat s názvem stejným, plně zadané sestavení "myApp.resources, verze = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a". Všimněte si, že pomocí místní aktualizace na soubory satelitní sestavení ztěžuje aplikace přesně určit verzi satelitní sestavení.  
  
 Další informace o správě verzí sestavení najdete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md) a [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>Načítání prostředků z soubory .resources  
 Pokud se rozhodnete, že není nasazujte prostředky v satelitní sestavení, které můžete použít <xref:System.Resources.ResourceManager> objektu pro přístup k prostředkům ze .resources soubory přímo. Chcete-li to provést, musíte nasadit soubory .resources správně. Potom pomocí <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metoda pro vytvoření instance <xref:System.Resources.ResourceManager> objektu a zadejte adresář obsahující soubory .resources samostatné.  
  
### <a name="deploying-resources-files"></a>Nasazení soubory .resources  
 Když vložíte soubory .resources sestavení aplikace a satelitní sestavení, každé satelitní sestavení má stejný název souboru, ale je umístěn v podadresáři, která odráží jazykovou verzi satelitní sestavení. Naproti tomu při přístupu k prostředkům soubory .resources přímo, můžete umístit všechny soubory .resources v jednom adresáři, obvykle podadresáři adresáře aplikace. Název souboru .resources výchozí aplikace se skládá z název kořenové, se žádná informace o jeho jazykové verze (například strings.resources). Prostředky pro jednotlivé lokalizované jazykové verze jsou uloženy v souboru, jehož název se skládá z název kořenové, za nímž následuje jazyková verze (například strings.ja.resources nebo strings.de DE.resources). Následující obrázek ukazuje, kde soubory prostředků, musí se nacházet ve strukturu adresáře.  
  
 ![Hlavní adresář pro vaši aplikaci](../../../docs/framework/resources/media/resappdir.gif "resappdir")  
Struktura adresáře a konvence pojmenování pro soubory .resources  
  
### <a name="using-the-resource-manager"></a>Pomocí Správce prostředků  
 Poté, co jste vytvořili vaše prostředky a je umístěn v adresáři odpovídající, vytvoříte <xref:System.Resources.ResourceManager> objekt, který chcete používat prostředky voláním <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metoda. První parametr určuje název kořenového souboru .resources výchozí aplikace (to by být "řetězce", například v předchozí části). Druhý parametr určuje umístění prostředků ("zdroje" pro předchozí příklad). Třetí parametr určuje <xref:System.Resources.ResourceSet> implementace používat. Pokud je třetí parametr `null`, modul runtime výchozí <xref:System.Resources.ResourceSet> se používá.  
  
> [!NOTE]
>  Nenasazujte aplikace ASP.NET pomocí samostatné soubory .resources. To může způsobit uzamčení problémy a zalomení XCOPY nasazení. Doporučujeme nasadit prostředky ve satelitní sestavení. Další informace najdete v tématu [webové stránky ASP.NET: Přehled prostředků](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd).  
  
 Po instanci můžete vytvořit <xref:System.Resources.ResourceManager> objekt, můžete použít <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, a <xref:System.Resources.ResourceManager.GetStream%2A> metody popsané dříve k načtení prostředků. Načítání prostředků přímo z soubory .resources se ale liší od načtení vložené prostředky ze sestavení. Při načítání prostředků z soubory .resources <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, a <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody vždy načíst výchozí jazykovou verzi prostředky bez ohledu na aktuální jazykové verze. K načtení prostředků pro aktuální jazykovou verzi buď aplikace nebo konkrétní jazykové verze, musí volat <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, nebo <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metoda a zadat jazykovou verzi, jejíž prostředky se mají být načteny. K načtení prostředků aktuální jazykové verze, zadejte hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost jako `culture` argument. Pokud správce prostředků nelze načíst z prostředků `culture`, používá záložní pravidel standardní prostředků pro načtení s příslušnými prostředky.  
  
### <a name="an-example"></a>Příklad  
 Následující příklad ilustruje, jak správce prostředků načte prostředky přímo z soubory .resources. V příkladu se skládá z tři založený na textu zdrojové soubory pro angličtinu (Spojené státy), francouzština (Francie) a ruskými jazykové verze. V příkladu výchozí jazykovou verzi je angličtina (Spojené státy). Jeho prostředky jsou uloženy v následující soubor s názvem Strings.txt:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Prostředky pro jazykovou verzi francouzština (Francie) jsou uloženy v následující soubor, který se nazývá Strings.fr-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Prostředky pro jazykovou verzi ruskými jsou uloženy v následující soubor, který se nazývá Strings.ru-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Následuje zdrojový kód pro tento příklad. Tento příklad vytvoří <xref:System.Globalization.CultureInfo> objektů pro angličtinu (Spojené státy), angličtina (Kanada), francouzština (Francie) a ruskými jazykové verze a díky každý aktuální jazykovou verzi. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Metoda pak poskytuje hodnotu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost jako `culture` argument načíst s příslušnými prostředky specifické pro jazykovou verzi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Verze jazyka C# v příkladu můžete zkompilovat spuštěním následující dávkového souboru. Pokud používáte Visual Basic, nahraďte `csc` s `vbc`a nahraďte `.cs` rozšíření s `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Resources.ResourceManager>  
 [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Vytváření a načítání prostředků v aplikacích pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=241674)
