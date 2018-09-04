---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 07/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628c571ce645710482a29c813adb4fe1a59fd349
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554633"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Vývoj napříč platformami pomocí přenosné knihovny tříd
Typ projektu knihovny přenosných tříd rozhraní .NET Framework v sadě Visual Studio pomáhá rychle a snadno vytvářet aplikace pro různé platformy a knihovny pro platformy Microsoft.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Přenosné knihovny tříd můžete zkrátit čas a náklady na vývoj a testování kódu. Použít tento typ projektu můžete zapisovat a sestavovat přenosná sestavení rozhraní .NET Framework a odkázat na tato sestavení z aplikace, které se vyvíjet pro víc platforem, jako je například Windows a Windows Phone.  
  
 I po vytvoření projektu přenosné knihovny tříd v sadě Visual Studio a začít s vývojem ho můžete změnit cílové platformy. Sada Visual Studio zkompiluje knihovny pomocí nové sestavení, který vám pomůže identifikovat změny, které je třeba provést v kódu.  
  
 Tento článek popisuje vývoj aplikací v sadě Visual Studio, ale Microsoft také poskytuje referenční sestavení knihovny přenosných tříd, které můžete použít k vývoji aplikací a knihovny se zmírněními hrozeb jiných nástrojů, například Xamarin. Tyto aplikace a knihovny můžete použít na všechny založené na platformě .NET runtime v jiné platformy než Microsoft. Další informace o referenční sestavení, naleznete v příspěvku blogu [Přenosná knihovna tříd (PCL) nyní k dispozici na všech platformách](https://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Chcete-li stáhnout sestavení, naleznete v tématu [Microsoft .NET Portable Library referenční sestavení](https://www.microsoft.com/download/details.aspx?id=40727) webu Microsoft Download Center. Další informace o tom, jak používat sestavení s využitím kódu Xamarin, najdete v příspěvku na blogu [NuGet knihoven .NET pro Xamarin nyní k dispozici a PCL](https://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Visual Studio poskytuje šablony, které vám pomůžou s vývojem pomocí přenosné knihovny tříd. V závislosti na tom, kterou verzi sady Visual Studio používáte dostupné šablony a nabídky lišit od těch popsaných v tomto článku.  
  
> [!WARNING]
>  Visual Studio 2013 Update 2 zahrnuje aktualizace knihovny přenosných tříd šablon. Pokud máte starší verzi sady Visual Studio a nainstalovanou sadu Visual Studio 2013 na stejném počítači, a pak nainstalujte Update 2, aby se změny **Cílová architektura** možností se použijí pro obě verze systému Visual Studio.  
  
 V tomto tématu:  
  
 [Visual Studio – podpora](#vs_support)  
 [Vytvoření projektu knihovny přenosných tříd](#create_pcl)  
 [Target – možnosti](#platforms)  
 [Změna cíle](#change_targets)  
 [Podporované funkce](#features)  
 [Podporované typy a členy](#members)  
 [API – rozdíly v přenosné knihovně tříd](#API_diff)  
 [Používání knihovny přenosných tříd](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Visual Studio – podpora  
 Visual Studio – podpora pro přenosné knihovny tříd závisí na verzi sady Visual Studio, kterou používáte. V některých případech budete mít všechno, co potřebujete, a v ostatních případech bude nutné nainstalovat další položky, jak je znázorněno v následující tabulce.  
  
|SKU sady Visual Studio|Podpora pro vytvoření přenosné knihovny tříd|  
|-----------------------|---------------------------------------------------|  
|Visual Studio 2010, Professional, Premium nebo Ultimate|Ano, když instalujete [Portable Library Tools](https://marketplace.visualstudio.com/items?itemName=BCLTeam.PortableLibraryTools2).|  
|Verze Visual Studio Express 2010.|Ne.|  
|Visual Studio 2012 Professional, Premium nebo Ultimate|Ano. Podpora Windows Phone 8.0, nainstalujte [Windows Phone SDK 8.0](https://www.microsoft.com/download/details.aspx?id=35471).|  
|Verze Visual Studio Express 2012|Ne.|  
|Visual Studio 2013 Professional, Premium nebo Ultimate|Ano. Podpora Windows Phone 8.1 instalovat [nejnovější verzi sady Visual Studio 2013](https://visualstudio.microsoft.com/vs/older-downloads/).|  
|Visual Studio Community 2013 pro Windows|Ano, když instalujete [nejnovější verzi sady Visual Studio Community 2013](https://visualstudio.microsoft.com/vs/older-downloads/), což zahrnuje aktualizaci Update 2.|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Vytvoření projektu knihovny přenosných tříd  
 K vytvoření přenosné knihovny tříd, by měl používat jednu z šablon, které jsou k dispozici v sadě Visual Studio. Vytvořte nový projekt a **nový projekt** dialogovém okně **šablony**, vyberte cílový jazyk (C# nebo Visual Basic) a pak vyberte jeden z cílových platforem. V dalším kroku můžete vybrat další platformy.  
  
 V aplikaci Visual Studio 2013 Update 2, můžete **knihovna tříd (přenosná)** šablony pro zvolený jazyk a platformu pro vytváření knihovny přenosných tříd. Zobrazí se vám tato šablona pro tyto platformy:  
  
-   Aplikace pro Store  
  
-   Plocha Windows  
  
-   Silverlight  
  
 Pokud chcete vytvořit knihovnu na cíl Windows Phone 8.1 a Windows 8.1 v C#, můžete zvolit **Store aplikace**a klikněte na tlačítko **knihovna tříd (přenosná a univerzální aplikace)**.  
  
 ![Knihovny přenosných tříd pro aplikace pro Store](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Tato šablona automaticky vybere Windows 8.1 a Windows Phone 8.1 jako cíle. Pokud vytvoříte knihovnu, která se zaměřuje jenom na Windows Phone 8.1 nebo Windows 8.1, můžete změnit cílové platformy a později přidat platformy.  
  
 Pokud používáte sadu Visual Studio 2012 nebo Visual Studio 2013 bez Update 2, vytvořte nový projekt a zvolte **přenosné knihovny tříd** šablony v jazyce Visual C# nebo Visual Basic.  
  
 ![Vyberte projektu přenosné knihovny](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Přidat přenosnou knihovnu tříd** zobrazí se dialogové okno a vybrat další platformy. Dialogové okno vám poskytne upozornění na kompatibilitu na základě cílů, které vyberete.  
  
 ![Změna cílové architektury dialogové okno pro VS2013](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Přidat přenosnou knihovnu tříd – dialogové okno pro Visual Studio 2013 Update 2  
  
 Bez ohledu na to, zda používáte Visual Studio 2012 nebo Visual Studio 2013 můžete vybrat platformy, při vytváření projektu přenosné knihovny tříd nebo vlastností projektu můžete změnit cílové platformy, po vytvoření projektu.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>Target – možnosti  
 Při vytváření projektu knihovny přenosných tříd můžete operační systém a verzi rozhraní .NET Framework, kterou chcete cílit. Pokud používáte Visual Studio 2013 a jste nainstalovali aktualizaci Update 2 nebo novější, můžete použít **knihovna tříd (přenosná a univerzální aplikace)** šablony k vytvoření přenosné knihovny tříd, který cílí na Windows 8.1 a Windows Phone 8.1. V následující tabulce jsou uvedeny dostupných cílů v závislosti na verzi sady Visual Studio, kterou používáte.  
  
|Target – možnost|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Update 2 nebo novější|  
|-|-|-|-|  
|.NET Framework|– .NET framework 4 a vyšší<br /><br /> – .NET framework 4.0.3 a vyšší<br /><br /> – .NET framework 4.5|– .NET framework 4 a vyšší<br /><br /> – .NET framework 4.0.3 a vyšší<br /><br /> – .NET framework 4.5 a vyšší<br /><br /> – .NET framework 4.5.1|– .NET framework 4<br /><br /> – .NET framework 4.0.3<br /><br /> – .NET framework 4.5<br /><br /> – .NET framework 4.5.1|  
|Windows Phone|– Windows Phone 7 a vyšší<br /><br /> – Windows Phone 7.5 a vyšší<br /><br /> – Windows Phone 8|– Windows Phone 8|– Windows Phone Silverlight 8<br /><br /> – Windows Phone Silverlight 8.1<br /><br /> Podpora prostředí Windows Runtime a XAML zvolte možnost:<br /><br /> – Windows Phone 8.1|  
|Windows Store|– .NET pro aplikace Windows Store|– Windows Store Apps (Windows 8) a vyšší<br /><br /> – Windows Store Apps (Windows 8.1)|– Windows 8<br /><br /> – Windows 8.1|  
|-Silverlight|-Silverlight 4 a vyšší<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Xbox 360|Není k dispozici|Není k dispozici|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Změna cíle  
 Výběr šablony přenosné knihovny tříd, výchozí platformy jsou vybrány pro vás, ale tyto výchozí hodnoty se budou lišit v závislosti na tom, kterou verzi sady Visual Studio jste si nainstalovali a cíle, které jste zvolili dříve. Platformy můžete změnit po vytvoření přenosné knihovny tříd nebo poté, co jste začali vývoj přenosné knihovny tříd.  
  
 Pokud chcete změnit cíle po vytvoření projektu v **Průzkumníka řešení**, otevřete místní nabídku projektu přenosné knihovny tříd (nikoli řešení) a klikněte na tlačítko **vlastnosti** . Na stránce Vlastnosti projektu **knihovny** karta zobrazuje platformy, že aktuálně váš projekt cílí.  
  
 ![Vlastnosti projektu](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Přenosné knihovny tříd stránku vlastností pro Visual Studio 2013 Update 2  
  
 Chcete-li přidat nebo odebrat cíle, zvolte **změnu** tlačítko a potom vyberte a zrušte zaškrtnutí příslušných políček.  
  
 Při změně cíle, které rozhraní API, která jsou k dispozici pro vývoj projektu se změní podle vašeho výběru. Visual Studio hlásí chyby a upozornění, které mohou nastat v důsledku změny cíle.  
  
 Pokud chcete vyhodnotit přenositelnost vašeho sestavení před provádět změny v sadě Visual Studio, můžete použít [.NET Portability Analyzeru](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Nabídka možnosti se budou lišit v závislosti na verzi sady Visual Studio, kterou používáte.  
  
 ![Změnit cíl](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Dialogové okno cíle změn v sadě Visual Studio 2012  
  
<a name="features"></a>   
## <a name="supported-features"></a>Podporované funkce  
 Následující tabulka zobrazuje podporované funkce dostupných platforem a verzí. V některých případech společnost Microsoft přidala podporu verze balíčku NuGet a byly zjištěny. Další informace o balíčcích NuGet pro rozhraní .NET Framework naleznete v tématu [The .NET Framework a vydání Out-of-Band](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Funkce|.NET Framework|.NET Framework|.NET Framework|Windows Store|Windows Store|Windows Phone Store|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Základní knihovny|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Podpora asynchronního|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Komprese|||✓|✓|✓|✓||➋|➋||||  
|Datové poznámky||✓|✓|✓|✓|||||✓|✓||  
|Dynamické klíčové slovo|✓|✓|✓|✓|✓|||||✓|✓||  
|HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|LINQ (Language-Integrated Query)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Managed Extensibility sítě (MEF)|✓|✓|✓|✓|✓|||||✓|✓||  
|Knihovna síťové třídy (NCL)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Serializace (kontraktu dat, XML a JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Zobrazit modely (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Rozhraní API Windows Runtime|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 Vyžaduje ➊ [Microsoft asynchronní](https://www.nuget.org/packages/Microsoft.Bcl.Async/) balíčku  
 Vyžaduje ➋ [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) balíčku  
 Vyžaduje ➌ [knihovny klienta HTTP Microsoft](https://www.nuget.org/packages/Microsoft.Net.Http) balíčku  
  
> [!WARNING]
>  Chyby mohou nastat, když odkazujete [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) a [knihovny klienta HTTP Microsoft](https://www.nuget.org/packages/Microsoft.Net.Http) balíčků z přenosné knihovny používat aplikace pro Windows Phone Silverlight 8.1. Další informace najdete v tématu [kompatibilita platformy a zásadní změny pro aplikace pro Windows Phone Silverlight 8.1](https://docs.microsoft.com/previous-versions/windows/apps/dn642084(v=vs.105)).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Podporované typy a členy  
 Typy a členy, které jsou k dispozici v projektech knihovny přenosných tříd jsou omezeny několika faktory kompatibility:  
  
-   Musí být sdíleny napříč cíli, který jste vybrali.  
  
-   Musí chovat podobně napříč těmito cíli.  
  
-   Nesmí se jednat o kandidáty na vyřazení.  
  
-   Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.  
  
 Například přenosné knihovny tříd obsahuje typy související s Uživatelským rozhraním pouze při použití prostředí Windows 8.1 a Windows Phone 8.1. Omezení může dojít také, pokud cílíte platformy (například Xbox, .NET Framework 4 a Windows Phone 7), které byly vydány před zavedením knihovny přenosných tříd. Rozhraní .NET Framework verze balíčků prostřednictvím balíčku NuGet, který zlepšuje podporu knihovny přenosných tříd pro některé z těchto starších platformách. Seznam balíčků NuGet a další informace najdete v tématu [The .NET Framework a vydání Out-of-Band](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Pokud člen je podporován v přenosné knihovny tříd a pro vybrané cíle, zobrazí se v projektu v technologii IntelliSense. Kromě toho, na ikonu přenosné knihovny tříd ![podporuje přenosné knihovny](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") se zobrazí v tabulce členů v [knihovna tříd rozhraní .NET Framework](https://msdn.microsoft.com/library/mt472912.aspx) vedle podporované členy. Například následující členy tabulka ukazuje, že <xref:System.String.Chars%2A> vlastnost <xref:System.String> třída je podporována v přenosné knihovně tříd:  
  
 ![Podporované ikony členu](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Ikona knihovny přenosných tříd  
  
 Můžete také podívat **informace o verzi** části referenčního tématu a vyhledat poznámku určující, že typ nebo člen je podporován v projektu knihovny přenosných tříd:  
  
 ![Informace o verzi přenosné knihovny](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Příklad – informace o verzi  
  
 Nezapomeňte však, že rozhraní API může nepodporuje v přenosné knihovně tříd, ale, zda můžete použít rozhraní API závisí na cíle, které můžete vybrat.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>API – rozdíly v přenosné knihovně tříd  
 Chcete-li sestavení knihovny přenosných tříd kompatibilní na všech podporovaných platformách, změna některých členů se poněkud in Portable Class Library.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Používání přenosné knihovny tříd  
 Po vytvoření projektu knihovny přenosných tříd něj můžete odkazovat z jiných projektů. Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.  
  
 Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, požadovaná verze (nebo novější) verze cílových platforem musí být nainstalován v počítači. Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci bez další úpravy spustit na počítači, který jste použili při vývoji aplikace.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Nasazení aplikace Windows Store nebo Windows Phone  
 Při vytváření aplikace Windows Phone a Windows store, která odkazuje na sestavení knihovny přenosných tříd, všechno, co potřebujete k nasazení aplikace je součástí balíčku aplikace a nejsou vyžadovány žádné další kroky.  
  
### <a name="deploying-a-net-framework-app"></a>Nasazení .NET Framework aplikace  
 Když nasadíte aplikaci .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, je nutné určit závislost na správnou verzi rozhraní .NET Framework. Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací. Pokud je cílem rozhraní .NET Framework 4 nebo novější, na počítači musí být rozhraní .NET Framework 4 s [aktualizovat](https://www.microsoft.com/download/details.aspx?id=3556), aktualizací 4.0.3 pro rozhraní .NET Framework 4 nebo .NET Framework 4.5 nainstalované.  
  
-   Vytvoření závislosti s nasazením ClickOnce: V **Průzkumníka řešení**, zvolte uzel projektu pro projekt, kterou chcete publikovat. (Jedná se o projekt, který odkazuje na projekt knihovny přenosných tříd.) V panelu nabídky zvolte **projektu**, **vlastnosti**a klikněte na tlačítko **publikovat** kartu. Na **publikovat** zvolte **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework (nebo aktualizace rozhraní .NET Framework 4).  
  
-   Vytvoření závislosti pomocí projektu instalace: V **Průzkumníka řešení**, vyberte projekt instalace. V panelu nabídky zvolte **projektu**, **vlastnosti**, **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.  
  
 Další informace o nasazení aplikací rozhraní .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Nasazení aplikace založené na technologii Silverlight  
 Když nasadíte aplikaci založené na technologii Silverlight, který odkazuje na sestavení knihovny přenosných tříd, musíte zajistit, že minimální verze modulu runtime potřebné pro aplikaci odpovídala její cílové verzi. Pokud je cílem aplikace Silverlight 4, musí mít verzi 4.0.60129.0 nebo vyšší. Verzi nastavíte zahrnutím `<param name="minRuntimeVersion" value="4.0.60129.0" />` na webové stránce, který je hostitelem aplikace založené na technologii Silverlight, následujícím způsobem:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="https://www.microsoft.com/getsilverlight/get-started/install/"   
             style="text-decoration:none">  
      <img src=http://download.microsoft.com/download/5/1/6/5165823D-1D79-4871-8AC2-42DDDB94A5C2/PNGs/SLMedallion_ENU.png  
             alt="Get Microsoft Silverlight" style="border-style:none"/>  
    </a>  
  </object>  
   <iframe id="_sl_historyFrame"   
              style="visibility:hidden;height:0px;width:0px;border:0px">  
   </iframe>  
</div>  
```  
  
## <a name="see-also"></a>Viz také  
 [Používání knihovny přenosných tříd spolu s modelem MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)  
 [Prostředky aplikací pro knihovny cílené na více platforem](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)  
 [.NET portability Analyzeru](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Nasazení](../../../docs/framework/deployment/net-framework-applications.md)
