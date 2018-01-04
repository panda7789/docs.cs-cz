---
title: "Vývoj napříč platformami pomocí přenosné knihovny tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
caps.latest.revision: "95"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 893bbc94d909d5c94b7f8727912a298575617c2c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Vývoj napříč platformami pomocí přenosné knihovny tříd
Přenosná knihovna tříd rozhraní .NET Framework typ projektu v sadě Visual Studio vám usnadní vytváření aplikací pro různé platformy a knihovny pro platformy Microsoft snadno a rychle.  
  
 Knihovny přenosných tříd vám může pomoct snížit čas a náklady na vývoj a testování kódu. Použít tento typ projektu k zápisu a sestavení přenosné sestavení rozhraní .NET Framework a poté odkazovat tato sestavení z aplikací, které cílí na více platforem, jako je například Windows a Windows Phone.  
  
 I po vytvoření projektu knihovny přenosných tříd v sadě Visual Studio a začít vyvíjet ho můžete změnit na cílové platformy. Visual Studio zkompiluje vaše knihovna s nové sestavení, která pomáhá identifikovat změny, které musíte udělat v kódu.  
  
 Tento článek popisuje vývoj aplikací v sadě Visual Studio, ale Microsoft také poskytuje referenční sestavení knihovny přenosných tříd, které můžete použít k vývoji aplikací a knihovny pomocí jiných nástrojů, jako je například Xamarin. Tyto aplikace a knihovny můžete použít na všechny runtime založené na rozhraní .NET Framework na platformách jiných společností než Microsoft. Další informace o referenční sestavení, naleznete v příspěvku blogu [přenosných třída knihovny PCL () nyní k dispozici na všech platformách](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Si můžete stáhnout sestavení [Microsoft .NET přenosné knihovny referenční sestavení](http://www.microsoft.com/download/details.aspx?id=40727) na webu Microsoft Download Center. Další informace o použití sestavení s Xamarinem, naleznete v příspěvku blogu [PCL a NuGet knihovny .NET pro Xamarin nyní k dispozici](http://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Visual Studio poskytuje šablony, které umožňují vývoj pomocí přenosné knihovny tříd. V závislosti na tom, která verze sady Visual Studio používáte dostupných šablon a nabídky se může lišit od těch popsaných v tomto článku.  
  
> [!WARNING]
>  [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace do knihovny přenosných tříd šablon. Pokud máte na dřívější verzi Visual Studio a Visual Studio 2013 nainstalovaná na stejném počítači, a pak nainstalujte Update 2, budou změny provedené **cílové rozhraní** volby se použijí pro obě verze sady Visual Studio.  
  
 V tomto tématu:  
  
 [Visual Studio – podpora](#vs_support)  
 [Vytvoření projektu knihovny přenosných tříd](#create_pcl)  
 [Target – možnosti](#platforms)  
 [Změna cíle](#change_targets)  
 [Podporované funkce](#features)  
 [Podporované typy a členy](#members)  
 [Rozhraní API rozdíly v Přenosná knihovna tříd](#API_diff)  
 [Používání knihovny přenosných tříd](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Visual Studio – podpora  
 Visual Studio – podpora pro přenosné knihovny tříd závisí na verzi sady Visual Studio používáte. V některých případech budete mít všechno, co potřebujete, a v ostatních případech budete muset nainstalovat další položky, jak je znázorněno v následující tabulce.  
  
|Visual Studio SKU|Podpora pro vytvoření přenosné knihovny tříd|  
|-----------------------|---------------------------------------------------|  
|Visual Studio 2010, Professional, Premium nebo Ultimate|Ano, když instalujete [přenosné knihovny nástroje](http://go.microsoft.com/fwlink/?LinkId=210823).|  
|Verze Visual Studio Express 2010.|Ne.|  
|Visual Studio 2012 Professional, Premium nebo Ultimate|Ano. Pro telefonickou podporu, nainstalujte [Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=265772).|  
|Visual Studio Express 2012 verze|Ne.|  
|Visual Studio 2013 Professional, Premium nebo Ultimate|Ano. Pro podporu Windows Phone 8.1 instalovat [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
|Visual Studio Express 2013 for Windows|Ano, když instalujete [nejnovější verzi sady Visual Studio Express](http://go.microsoft.com/fwlink/p/?LinkId=394629), což zahrnuje Update 2, nebo přidejte [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Vytvoření projektu knihovny přenosných tříd  
 K vytvoření přenosné knihovny tříd, používejte jednu z šablon, zadaný v sadě Visual Studio. Vytvořte nový projekt a v **nový projekt** dialogovém **šablony**, vyberte svůj jazyk cíl (C# nebo Visual Basic) a pak vyberte jeden z platformy, které chcete cílit. V dalším kroku můžete vybrat další platformy.  
  
 V sadě Visual Studio 2013 Update 2, můžete **knihovny tříd (přenositelností)** šablonu pro vybraný jazyk a platformu pro vytvoření knihovny přenosných tříd. Zobrazí se tato šablona pro tyto platformy:  
  
-   Aplikace pro Store  
  
-   Windows Desktop  
  
-   Silverlight  
  
 Pokud chcete vytvořit knihovnu, kterou chcete cíl Windows Phone 8.1 a Windows 8.1 v jazyce C#, můžete vybrat **aplikací ze Storu**a potom zvolte **knihovny tříd (přenositelností pro univerzální aplikace pro)**.  
  
 ![Knihovny přenosných tříd pro aplikace pro Store](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Tato šablona automaticky vybere Windows 8.1 a Windows Phone 8.1 jako cíle. Pokud vytvoříte knihovny, které se zaměřuje jenom Windows Phone 8.1 nebo Windows 8.1, můžete změnit na cílové platformy a později přidat platformy.  
  
 Pokud používáte Visual Studio 2012 nebo Visual Studio 2013 bez Update 2, vytvořte nový projekt a zvolte **Přenosná knihovna tříd** šablony v jazyce Visual C# nebo Visual Basic.  
  
 ![Vyberte projekt přenosné knihovny](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Přidat Přenosná knihovna tříd** zobrazí se dialogové okno a vybrat další platformy. Dialogové okno vám poskytne kompatibility upozornění na základě cílů, které vyberete.  
  
 ![Změna cílové architektury dialogové okno pro VS2013](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Přenosná knihovna tříd dialogové okno Přidat pro Visual Studio 2013 Update 2  
  
 Bez ohledu na to, zda používáte Visual Studio 2012 nebo Visual Studio 2013 můžete vybrat platformy, při vytváření projektu knihovny přenosných tříd nebo vlastností projektu můžete použít k úpravě cílových platforem po vytvoření projektu.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>Target – možnosti  
 Při vytváření projektu knihovny přenosných tříd, můžete operační systém a verze rozhraní .NET Framework, kterou chcete zacílit. Pokud používáte Visual Studio 2013 a instalaci aktualizací 2 nebo novější, můžete **knihovny tříd (přenositelností pro univerzální aplikace pro)** šablony k vytvoření přenosné knihovny tříd, která je cílena Windows 8.1 a Windows Phone 8.1. V následující tabulce jsou k dispozici cíle v závislosti na verzi Visual Studia, kterou používáte.  
  
|– Možnost cílové|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Update 2 nebo novější|  
|-|-|-|-|  
|.NET Framework|-Rozhraní .NET framework 4 a vyšší<br /><br /> -Rozhraní .NET framework 4.0.3 a vyšší<br /><br /> -Rozhraní .NET framework 4.5|-Rozhraní .NET framework 4 a vyšší<br /><br /> -Rozhraní .NET framework 4.0.3 a vyšší<br /><br /> -Rozhraní .NET framework 4.5 a vyšší<br /><br /> -Rozhraní .NET framework 4.5.1|-Rozhraní .NET framework 4<br /><br /> -Rozhraní .NET framework 4.0.3<br /><br /> -Rozhraní .NET framework 4.5<br /><br /> -Rozhraní .NET framework 4.5.1|  
|Windows Phone|– Windows Phone 7 a vyšší<br /><br /> – Windows Phone 7.5 a novější<br /><br /> – Windows Phone 8|– Windows Phone 8|– Windows Phone Silverlight 8<br /><br /> – Windows Phone Silverlight 8.1<br /><br /> Podpora prostředí Windows Runtime a XAML vyberte:<br /><br /> – Windows Phone 8.1|  
|Windows Store|-.NET pro aplikace pro Windows Store|– Aplikace Windows Store (Windows 8) a vyšší<br /><br /> – Aplikace Windows Store (Windows 8.1)|– Windows 8<br /><br /> – Windows 8.1|  
|-Silverlight|-Silverlight 4 a vyšší<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Xbox 360|Není k dispozici|Není k dispozici|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Změna cíle  
 Vyberte šablonu Přenosná knihovna tříd, jsou pro vás vybrané výchozí platformy, ale tato výchozí nastavení se budou lišit v závislosti na tom, která verze sady Visual Studio jste nainstalovali a cíle, které jste vybrali dříve. Platformy můžete změnit, když vytvoříte Přenosná knihovna tříd nebo po zahájením vývoj přenosné knihovny tříd.  
  
 Pokud chcete změnit cíle po vytvoření projektu v **Průzkumníku řešení**, otevřete místní nabídky projektu knihovny přenosných tříd (ne řešení) a potom zvolte **vlastnosti** . Na stránce vlastností projektu **knihovny** kartě se zobrazují platformy aktuálně cílem vašeho projektu.  
  
 ![Vlastnosti projektu](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Přenosná knihovna tříd stránka vlastností pro Visual Studio 2013 Update 2  
  
 Chcete-li přidat nebo odebrat cíle, zvolte **změnu** tlačítko a poté vyberte a zrušte zaškrtnutí políčka.  
  
 Při změně cíle pro rozhraní API, které jsou k dispozici pro vývoj projektu se změní podle vašeho výběru. Visual Studio nahlásí chyby a upozornění, která může nastat v důsledku Změna cíle.  
  
 Pokud chcete vyhodnotit přenositelnost vaše sestavení před zahájením proveďte změny v sadě Visual Studio, můžete použít [.NET přenositelnost analyzátor](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Možnosti nabídky se budou lišit v závislosti na verzi Visual Studia, kterou používáte.  
  
 ![Změna cílové](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Dialogové okno cíle změny v sadě Visual Studio 2012  
  
<a name="features"></a>   
## <a name="supported-features"></a>Podporované funkce  
 Následující tabulka zobrazuje podporované funkce dostupných platforem a verzí. V některých případech společnost Microsoft přidala podporu pro verzi balíčku NuGet, a to uvedeno. Další informace o balíčcích NuGet pro rozhraní .NET Framework najdete v tématu [rozhraní .NET Framework a Out-of-Band verze](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Funkce|.NET Framework|.NET Framework|.NET Framework|Windows Store|Windows Store|Windows Phone Store|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Základní knihovny|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Asynchronní podpora|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Komprese|||✓|✓|✓|✓||➋|➋||||  
|Datové poznámky||✓|✓|✓|✓|||||✓|✓||  
|Dynamické klíčové slovo|✓|✓|✓|✓|✓|||||✓|✓||  
|HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|LINQ (Language-Integrated Query)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Spravovaná rozšíření sítě (MEF)|✓|✓|✓|✓|✓|||||✓|✓||  
|Knihovna síťové třídy (NCL)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Serializace (kontrakt dat, XML a JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Zobrazit modely (modelem MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Rozhraní API systému Windows Runtime|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 Vyžaduje ➊ [Microsoft asynchronní](https://www.nuget.org/packages/Microsoft.Bcl.Async/) balíčku  
 Vyžaduje ➋ [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) balíčku  
 Vyžaduje ➌ [knihovny klienta HTTP Microsoft](http://www.nuget.org/packages/Microsoft.Net.Http) balíčku  
  
> [!WARNING]
>  Mohou nastat chyby, když odkazujete [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) a [knihovny klienta HTTP Microsoft](http://www.nuget.org/packages/Microsoft.Net.Http) balíčky z přenosné knihovny používá aplikace Windows Phone Silverlight 8.1. Další informace najdete v tématu [kompatibilita platformy a nejnovější změny pro aplikace Windows Phone Silverlight 8.1](http://go.microsoft.com/fwlink/p/?LinkId=394744).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Podporované typy a členy  
 Typy a členy, kteří jsou k dispozici v projektech Přenosná knihovna tříd jsou omezeny několika různými faktory kompatibility:  
  
-   Musí být sdílená mezi cíle, které jste vybrali.  
  
-   Je nutné chovají podobně napříč těchto cílů.  
  
-   Nesmí se jednat o kandidáty na vyřazení.  
  
-   Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.  
  
 Přenosná knihovna tříd například obsahuje typy související s uživatelského rozhraní, pouze v případě, že cílové Windows 8.1 a Windows Phone 8.1. Omezení mohou také nastat, pokud cílíte na platformy (třeba Xbox, rozhraní .NET Framework 4 a Windows Phone 7), které byly vydané dřív než zavedení Přenosná knihovna tříd. Rozhraní .NET Framework verze balíčky prostřednictvím balíčku NuGet, který zlepšuje podpory knihovny přenosných tříd pro některé z těchto starších platformách. Seznam balíčků NuGet a další informace najdete v tématu [rozhraní .NET Framework a Out-of-Band verze](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Pokud člen je podporován v přenosné knihovny tříd a pro vybrané cíle, zobrazí se ve vašem projektu v technologii IntelliSense. Kromě toho ikonu Přenosná knihovna tříd ![nepodporuje přenosné knihovny](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") se zobrazí v tabulkách členy v [rozhraní .NET Framework – knihovna tříd](http://go.microsoft.com/fwlink/?LinkId=211358) další podporované členy. Například následující členy tabulka ukazuje, že <xref:System.String.Chars%2A> vlastnost <xref:System.String> třída je podporována v Přenosná knihovna tříd:  
  
 ![Ikona podporované člen](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Ikona knihovny přenosných tříd  
  
 Můžete si také prohlédnout **informace o verzi** části referenční téma pro Poznámka, která udává, že typ nebo člen je podporována v projektu knihovny přenosných tříd:  
  
 ![Informace o verzi přenosné knihovny](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Například informace o verzi  
  
 Nezapomeňte však, že rozhraní API může být v Přenosná knihovna tříd podporovaná, ale jestli můžete použít rozhraní API závisí na cíle, můžete vybrat.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Rozhraní API rozdíly v Přenosná knihovna tříd  
 Chcete-li kompatibilní sestavení knihovny přenosných tříd pro všechny podporované platformy, některé členy se trochu změnily v Přenosná knihovna tříd.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Používání přenosné knihovny tříd  
 Po vytvoření projektu knihovny přenosných tříd můžete stačí na něj odkazovat z jiných projektů. Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.  
  
 Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, požadovaná verze (nebo novější) cílových platforem musí být nainstalován v počítači. Visual Studio obsahuje všechny požadované rozhraní, takže aplikaci bez další úpravy můžete spustit na počítači, který jste použili k vývoji aplikace.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Nasazení aplikace Windows Store nebo Windows Phone  
 Při vytváření Windows store nebo Windows Phone aplikace odkazující sestavení knihovny přenosných tříd, vše, co potřebujete k nasazení aplikace je součástí balíčku aplikace a nejsou potřeba žádné další kroky.  
  
### <a name="deploying-a-net-framework-app"></a>Nasazení .NET Framework aplikace  
 Když nasadíte aplikaci rozhraní .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, musíte zadat závislost na správnou verzi rozhraní .NET Framework. Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací. Pokud cílíte na rozhraní .NET Framework 4 nebo novější, počítač musí mít rozhraní .NET Framework 4 s [aktualizace](http://go.microsoft.com/fwlink/?LinkId=210824), aktualizace 4.0.3 pro rozhraní .NET Framework 4 nebo rozhraní .NET Framework 4.5 nainstalované.  
  
-   Postup vytvoření závislosti s nasazením ClickOnce: V **Průzkumníku**, vyberte uzel projektu pro projekt, kterou chcete publikovat. (To je projekt, který odkazuje na projekt knihovny přenosných tříd.) Na řádku nabídek zvolte **projektu**, **vlastnosti**a potom zvolte **publikovat** kartě. Na **publikovat** vyberte **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework (nebo aktualizace rozhraní .NET Framework 4).  
  
-   Postup vytvoření závislosti pomocí projektu instalace: V **Průzkumníku**, zvolte projektu. Na řádku nabídek zvolte **projektu**, **vlastnosti**, **požadavky**. Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.  
  
 Další informace o nasazování aplikací rozhraní .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Nasazení aplikace na základě Silverlight  
 Při nasazení aplikace založená na technologii Silverlight, který odkazuje na sestavení knihovny přenosných tříd, je nutné zajistit, že minimální runtime verze požadované aplikace odpovídá jeho cílovou verzi. Pokud je cílem aplikace Silverlight 4, musí mít verzi 4.0.60129.0 nebo vyšší. Nastavit verzi zahrnutím `<param name="minRuntimeVersion" value="4.0.60129.0" />` na webové stránce, který je hostitelem aplikace založená na technologii Silverlight, následujícím způsobem:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="http://go.microsoft.com/fwlink/?LinkID=149156&v=4.0.50826.0"   
             style="text-decoration:none">  
      <img src=http://go.microsoft.com/fwlink/?LinkId=161376  
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
 [Analyzátor přenositelnost rozhraní .NET](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Nasazení](../../../docs/framework/deployment/net-framework-applications.md)
