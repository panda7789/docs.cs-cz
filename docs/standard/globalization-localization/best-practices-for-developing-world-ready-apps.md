---
title: Doporučené postupy pro vývoj aplikací připravených k použití
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 804f92ddd564f057157598c3cf62106d1a7d5318
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578195"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Doporučené postupy pro vývoj aplikací připravených k použití
Tato část popisuje osvědčené postupy při vývoji aplikací připravených.  
  
## <a name="globalization-best-practices"></a>Osvědčené postupy globalizace  
  
1.  Aby vaše aplikace Unicode interně.  
  
2.  Použití třídy podporující jazykové verze poskytované <xref:System.Globalization> oboru názvů k manipulaci a formátování data.  
  
    -   Pro řazení, použijte <xref:System.Globalization.SortKey> třídy a <xref:System.Globalization.CompareInfo> třídy.  
  
    -   Pro porovnání řetězců, použijte <xref:System.Globalization.CompareInfo> třídy.  
  
    -   Pro formátování data a času, použijte <xref:System.Globalization.DateTimeFormatInfo> třídy.  
  
    -   Použít pro formátování čísel <xref:System.Globalization.NumberFormatInfo> třídy.  
  
    -   Pro gregoriánského a jiném než gregoriánském kalendáři, použijte <xref:System.Globalization.Calendar> třídy nebo některé z konkrétních implementací kalendáře.  
  
3.  Použít nastavení jazykové verze vlastnost od <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> – třída v příslušné situacích. Použití <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost pro formátování úlohy, jako je například datum a čas nebo formátování čísel. Použití <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost k načtení prostředků. Všimněte si, že `CurrentCulture` a `CurrentUICulture` vlastnosti lze nastavit na vlákno.  
  
4.  Povolení ke čtení a zápisu dat do a z různých kódování pomocí kódování třídy v aplikaci <xref:System.Text> oboru názvů. Nepředpokládejte ASCII data. Předpokládejme, že bude nutné zadat mezinárodní znaky kdekoli může uživatel zadat text. Například by měla aplikace přijímat mezinárodní znaky v názvů serverů, adresářů, názvy souborů, uživatelská jména a adresy URL.  
  
5.  Při použití <xref:System.Text.UTF8Encoding> třídy z bezpečnostních důvodů použití funkce rozpoznávání chyb, které nabízí tato třída. Zapnutí funkce rozpoznávání chyb, aplikace vytvoří instanci třídy pomocí konstruktor, který přebírá `throwOnInvalidBytes` parametr a nastaví hodnotu tohoto parametru k `true`.  
  
6.  Pokud je to možné, popisovač řetězce jako celé řetězce místo jako řadu jednotlivých znaků. To je zvlášť důležité při řazení nebo hledání dílčích řetězců. To zabrání problémy spojené s analýzou kombinovaných znaků.  
  
7.  Zobrazení textu s použitím třídy poskytované <xref:System.Drawing> oboru názvů.  
  
8.  Pro konzistenci mezi operační systémy, Nepovolovat nastavení uživatele přepsat <xref:System.Globalization.CultureInfo>. Použití `CultureInfo` konstruktor, který přijímá `useUserOverride` parametr a nastavte ji na `false`.  
  
9. Otestujte funkčnost aplikace na mezinárodní verze operačních systémů, pomocí mezinárodní data.  
  
10. Pokud rozhodnutí zabezpečení je na základě výsledku porovnání řetězců nebo změny velikosti písmen, máte aplikace provést operaci na jazykové verzi. Tento postup zajišťuje, že výsledek není ovlivněn hodnotu `CultureInfo.CurrentCulture`. Najdete v části "Řetězec porovnání, použijte aktuální jazykovou verzi" [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) pro příklad, který ukazuje, jak řetězců porovnání může způsobit nekonzistentní výsledky.  
  
## <a name="localization-best-practices"></a>Doporučené postupy pro lokalizaci  
  
1.  Přesuňte všechny lokalizovatelný prostředky k oddělení pouze prostředky. Lokalizovatelný prostředky zahrnují prvky uživatelského rozhraní, jako je například řetězce, chybové zprávy, dialogová okna, nabídky a prostředky vložený objekt.  
  
2.  To není závislé řetězce nebo prostředky uživatelského rozhraní.  
  
3.  Neumísťujte nelokalizovatelný prostředky do knihovny DLL určené pouze. To způsobuje nejasnosti překladatele.  
  
4.  Proveďte složené řetězce, které jsou vytvořené v době běhu ze spojených frází. Složené řetězce obtížně lokalizaci, protože často předpokládají anglické gramaticky pořadí, které se nevztahuje na všechny jazyky.  
  
5.  Vyhněte se nejednoznačný konstrukce, jako je například "Prázdnou složku", kde můžete řetězce přeložit odlišně v závislosti na gramaticky role součástí řetězec. Například "prázdný" může být operaci nebo přídavné jméno, což může vést k jiné převody v jazycích, jako je například italština nebo francouzština.  
  
6.  Nepoužívejte bitové kopie a ikony, které obsahují text ve vaší aplikaci. Jsou nákladné lokalizovat.  
  
7.  Poskytnout dostatek místa pro délku řetězce v uživatelském rozhraní. V některých jazycích frází může vyžadovat více místa, než budou potřebovat v dalších jazycích 50-75 procent.  
  
8.  Použití <xref:System.Resources.ResourceManager?displayProperty=nameWithType> k načtení prostředků na základě jazykovou verzi.  
  
9. Použijte sadu Visual Studio k vytvoření dialogová okna Windows Forms, tak, aby mohly být lokalizovány pomocí [Windows Forms – Editor prostředků (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Nevytvářejte ručně kód dialogová okna Windows Forms.  
  
10. Zajistěte profesionální lokalizaci (překlad).  
  
11. Úplný popis vytváření a lokalizace prostředků, najdete v části [prostředky v aplikacích](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>Globalizace osvědčené postupy pro aplikace ASP.NET  
  
1.  Explicitně nastavit <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> a <xref:System.Globalization.CultureInfo.CurrentCulture%2A> vlastnosti ve vaší aplikaci. Nespoléhejte na výchozí hodnoty.  
  
2.  Všimněte si, že aplikace ASP.NET jsou spravované aplikace a proto můžete použít stejné třídy jako ostatní spravované aplikace pro načítání, zobrazení a manipulace s nimi informace založené na jazykové verzi.  
  
3.  Uvědomte si, že je možné zadat následující tři typy kódování technologie ASP.NET:  
  
    -   requestEncoding určuje kódování přijaté z prohlížeče klienta.  
  
    -   responseEncoding určuje kódování k odeslání do prohlížeče klienta. Ve většině případů toto kódování musí být stejná jako zadaná pro requestEncoding.  
  
    -   fileEncoding určuje výchozí kódování pro .aspx, .asmx a .asax při analýze souboru.  
  
4.  Zadejte hodnoty pro atributy requestEncoding, responseEncoding, fileEncoding, culture a uiCulture v následujících třech místech v aplikaci ASP.NET:  
  
    -   V sekci globalizace v souboru Web.config. Tento soubor je externí aplikaci ASP.NET. Další informace najdete v tématu [ \<globalizace > Element](https://msdn.microsoft.com/library/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   V direktivě stránky. Všimněte si, že když aplikace na stránce, soubor je již přečtena. Proto je příliš pozdě zadat fileEncoding a requestEncoding. V direktivě stránky lze zadat pouze uiCulture, Culture a responseEncoding.  
  
    -   Prostřednictvím kódu programu v kódu aplikace. Toto nastavení se může lišit na základě požadavku. Jako u direktivy stránky, na době, aplikace je dosaženo kódu je příliš pozdě zadat fileEncoding a requestEncoding. V kódu aplikace lze zadat pouze uiCulture, Culture a responseEncoding.  
  
5.  Všimněte si, že hodnota uiCulture lze nastavit v prohlížeči přijmout jazyk.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
