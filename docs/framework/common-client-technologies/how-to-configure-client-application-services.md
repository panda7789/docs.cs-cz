---
title: 'Postupy: Konfigurace klientských aplikačních služeb'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8a6c6be6874c1a90c9e40b5b82d833aeaa9b63a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-client-application-services"></a>Postupy: Konfigurace klientských aplikačních služeb
Toto téma popisuje způsob použití sady Visual Studio **Návrhář projektu** povolit a nakonfigurovat klientské aplikační služby. Klient aplikačních služeb můžete použít k ověření uživatelů a načítání uživatelských rolí a nastavení z existující [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikace služby. Po konfiguraci, můžete přístup povolené služby v kódu aplikace, jak je popsáno v [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Další informace o [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační služby, najdete v části [aplikace ASP.NET: Přehled služby](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Můžete povolit a nakonfigurovat klientské aplikační služby na **služby** stránky **Návrhář projektu**. **Služby** stránka aktualizuje hodnoty v souboru App.config vašeho projektu. Pro přístup k **Návrhář projektu**, použijte **vlastnosti** příkaz na **projektu** nabídky. Další informace o **služby** stránky najdete v tématu [stránka služby, Návrhář projektu](https://msdn.microsoft.com/library/bb398109).  
  
 Následující postup popisuje, jak chcete provést základní konfiguraci pro klientské aplikační služby. Pokročilá konfigurace, které možnosti jsou popsané v dalších oddílech.  
  
### <a name="to-configure-client-application-services"></a>Konfigurace klientských aplikačních služeb  
  
1.  V **Průzkumníku řešení**, vyberte uzel projektu a pak na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     **Návrhář projektu** se zobrazí.  
  
2.  Klikněte **služby** kartě. **Služby** stránky se zobrazí, jak je znázorněno na následujícím obrázku.  
  
     ![Na kartě služeb v Návrháři projektu](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Na **služby** vyberte **povolit klientské aplikační služby**.  
  
    > [!NOTE]
    >  Klient aplikačních služeb vyžadují plnou verzi rozhraní .NET Framework a nejsou podporovány v profil klienta rozhraní .NET Framework. Pokud **povolit klientské aplikační služby** zaškrtávací políčko je zakázáno, ověřte, zda **cílové rozhraní** je nastaven na rozhraní .NET Framework 3.5 nebo novější. Chcete-li zobrazit **cílové rozhraní** nastavení v jazyce C#, otevřete v Návrháři projektu a klikněte **aplikace** stránky. Chcete-li zobrazit **cílové rozhraní** nastavení v jazyce Visual Basic, otevřete v Návrháři projektu, klikněte na **zkompilovat** a pak klikněte na tlačítko **Upřesnit možnosti kompilace**.  
  
4.  Vyberte **ověřování pomocí formulářů** Pokud budete chtít poskytnout vlastní ovládací prvky pro přihlášení nebo dialogové okno, nebo vyberte **ověřování systému Windows použít** na používání identity součástí operačního systému. Další informace najdete v tématu [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Pokud vyberete **ověřování systému Windows použít**, klient aplikačních služeb nakonfigurují automaticky používat databázi systému SQL Server Compact. To je uvedené v **pokročilé nastavení služeb** dialogové okno jak je popsáno v následující části. Pokud pak vyberete **ověřování pomocí formulářů**, **použít vlastní připojovací řetězec** nastavení nebude automaticky vymazána. To může vést k chybám, pokud [!INCLUDE[ssEW](../../../includes/ssew-md.md)] databáze již byla vytvořena pro použití s ověřováním systému Windows. Chcete-li opravte tyto chyby, zrušte **použít vlastní připojovací řetězec** nastavení v **pokročilé nastavení služeb** dialogové okno.  
  
5.  Pokud jste vybrali **ověřování pomocí formulářů**v **umístění služby ověřování** pole, zadejte adresu URL hostitele služby, není včetně názvu souboru. Návrháře automaticky připojí název souboru standardní (Authentication_JSON_AppService.axd) Pokud je hodnota zapisuje do konfiguračního souboru.  
  
6.  Případně pokud jste vybrali **ověřování pomocí formulářů**, můžete zadat hodnotu v **přihlašovací údaje poskytovatele** pole. Přihlašovací údaje poskytovatel musí implementovat <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. Pomocí poskytovatele přihlašovacích údajů můžete oddělit přihlášení uživatelského rozhraní od jiných kódu aplikace. Umožňuje vytvořit jeden přihlašovací dialogové okno pro použití v několika aplikací. Další informace najdete v tématu [postupy: implementace přihlášení uživatele u klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Pokud zadáte poskytovatele přihlašovacích údajů, zadejte je jako typ sestavení kvalifikovaný název. Další informace najdete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> a [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md). V nejjednodušší podobě název sestavení kvalifikovaný typ vypadá podobně jako v následujícím příkladu:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  V **role služby umístění** a **nastavení webové služby umístění** textová pole, zadejte umístění služby pro jednotlivé služby není včetně názvu souboru. Návrhář automaticky připojí názvy standardní souborů (Role_JSON_AppService.axd a Profile_JSON_AppService.axd) při zapíše hodnotu do konfiguračního souboru.  
  
8.  Volitelně klikněte na **Upřesnit** Změnit pokročilé nastavení, jako je například místní chování ukládání do mezipaměti. Další informace naleznete v následující proceduře.  
  
## <a name="advanced-configuration"></a>Pokročilá konfigurace  
 Následující postupy popisují postup konfigurace klientských aplikačních služeb pro méně běžné scénáře. Například můžete použít tyto možnosti konfigurace pro aplikace nasazené na veřejných místech, nebo pro databázi systému SQL Server Compact šifrovaná i místní datové mezipaměti.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Postup při konfiguraci rozšířených nastavení pro klientské aplikační služby  
  
1.  Na **služby** stránky **Návrhář projektu**, klikněte na tlačítko **Upřesnit**.  
  
     **Pokročilé nastavení služeb** dialogové okno se zobrazí, jak je znázorněno na následujícím obrázku. Další informace o dialogovém najdete v tématu [rozšířená nastavení pro dialogové okno služby](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Upřesňující nastavení pro dialogové okno služby](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Vyberte nebo zrušte **uložit hodnoty hash hesla místně pro povolení offline přihlášení**. Když vyberete tuto možnost, šifrovaném formátu hesla uživatele bude do mezipaměti místně. To je užitečné, pokud budete implementovat offline režimu pro vaši aplikaci. Tuto možnost, můžete ověřit uživatele i v případě <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> vlastnost byla nastavena na `true`.  
  
3.  Vyberte nebo zrušte **vyžadovat, aby se znovu přihlaste vždy, když vyprší platnost souboru cookie serveru uživatelé**. Ověřovacího souboru cookie je nakonfigurován na vzdálené služby a určuje, jak dlouho zůstane aktivní přihlášení uživatele. Další informace o tom, jak nakonfigurovat soubor cookie najdete v tématu `timeout` atribut [forms Element pro ověřování (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Pokud vyberete tuto možnost, pokusu o přístup k vzdálené role nebo vyvolá výjimku webové nastavení služby po vypršení platnosti souboru cookie pro ověřování <xref:System.Net.WebException>. Může zpracovat výjimku a zobrazit dialogové okno přihlášení s znovu ověřit uživatele. Příklad toto chování, naleznete v části [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Tato možnost je užitečná pro aplikace nasazené na veřejných místech, abyste měli jistotu, že uživatelé, kteří nechte aplikace spuštěna po použití zůstat ověří po neomezenou dobu.  
  
     Pokud zrušíte tuto možnost a pokus o přístup k vzdálené služby po vypršení platnosti souboru cookie pro ověřování, uživatelé budou automaticky znovu.  
  
4.  Zadejte hodnotu pro **časový limit mezipaměti služby Role**. Tento časový interval nastavená na hodnotu malé, když jsou aktualizovány role často nebo na hodnotu větší nebo když role jsou aktualizovány zřídka. Pokud budete implementovat offline režimu, nastavte časový interval pro velké hodnoty, aby se zabránilo informace o rolích z vypršení platnosti, zatímco aplikace v režimu offline.  
  
     Zprostředkovatele rolí přistupuje hodnoty v mezipaměti role nebo službu role při volání <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metoda. Prostřednictvím kódu programu obnovit do mezipaměti a vynutit tato metoda pro přístup ke vzdálené službě, volání <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metoda.  
  
5.  Vyberte nebo zrušte **použít vlastní připojovací řetězec**. Další informace naleznete v následující proceduře.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>Nakonfigurovat klientské aplikační služby na databázi použít místní mezipaměti  
  
1.  Na **služby** stránky **Návrhář projektu**, klikněte na tlačítko **Upřesnit**.  
  
     **Pokročilé nastavení služeb** zobrazí se dialogové okno.  
  
2.  Vyberte **použít vlastní připojovací řetězec**.  
  
     Výchozí hodnota `Data Source = |SQL/CE|` se zobrazí v textovém poli.  
  
3.  Pokud chcete vygenerovat a používat databázi systému SQL Server Compact, ponechte výchozí hodnotu řetězce připojení. Visual Studio bude generovat soubor databáze a umístí jej v adresáři indikován <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> vlastnost.  
  
4.  Generovat a používat šifrované [!INCLUDE[ssEW](../../../includes/ssew-md.md)] databáze, přidejte `password` a `encrypt database` hodnoty do připojovacího řetězce, jak je znázorněno v následujícím příkladu.  
  
    > [!NOTE]
    >  Nezapomeňte zadat silné heslo. Heslo nelze změnit po vygenerování databáze.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Pokud chcete používat vlastní databázi systému SQL Server, zadejte vlastní připojovací řetězec. Informace o formátech platný připojovací řetězec naleznete v dokumentaci k systému SQL Server. Tato databáze není generován automaticky. Připojovací řetězec musí odkazovat na existující databázi, která můžete vytvořit pomocí následujících příkazů SQL.  
  
    ```  
    CREATE TABLE ApplicationProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE UserProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE Roles (UserName nvarchar(256),   
        RoleName nvarchar(256))  
    CREATE TABLE Settings (PropertyName nvarchar(256),   
        PropertyStoredAs nvarchar(1), PropertyValue nvarchar(2048))  
    ```  
  
## <a name="using-custom-providers"></a>Použití vlastní zprostředkovatelé  
 Ve výchozím nastavení používá funkci klientských aplikací služby zprostředkovatele v <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> oboru názvů. Při konfiguraci vaší aplikace pomocí **služby** stránky **Návrhář projektu**, odkazy na tyto zprostředkovatele jsou přidány do souboru App.config. Tyto výchozí zprostředkovatele přístup odpovídající zprostředkovatele na serveru. Webové služby je často nakonfigurovaný pro přístup k datům uživatele prostřednictvím zprostředkovatele, jako <xref:System.Web.Security.SqlMembershipProvider> a <xref:System.Web.Security.SqlRoleProvider>.  
  
 Pokud chcete použít vlastní poskytovatelé, bude obvykle změnit zprostředkovatele na straně serveru, tak, aby mají vliv na všechny klientské aplikace, které přístup k serveru. Máte ale možnost pomocí jiného než výchozího zprostředkovatele na straně klienta. Vlastní zprostředkovatelé ověřování nebo role v souboru App.config vašeho projektu, můžete zadat, jak je znázorněno v následujícím postupu. Informace o tom, jak vytvořit vlastní ověřování a zprostředkovatelů rolí najdete v tématu [implementace poskytovatele členství](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) a [implementaci zprostředkovatele rolí](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Můžete použít také vlastní nastavení poskytovatele změnou vašeho projektu `Settings` – třída (přístup jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v jazyce Visual Basic). Další informace najdete v tématu [architektura nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>Konfigurace klientských aplikačních služeb používat jiného než výchozího zprostředkovatele  
  
1.  Pokud chcete použít jiné než výchozí ověřování nebo zprostředkovatel služby rolí, nejprve dokončit všechny ostatní nastavení konfigurace pomocí **služby** stránky.  
  
2.  Zavřít **Návrhář projektu**. To je nezbytné, protože **služby** stránka se automaticky aktualizuje souboru App.config i v případě, že měnit nastavení. Pokud jste ručně upravit souboru App.config, jak je popsáno v tomto postupu a pak se vraťte do **služby** stránky, vaše změny se resetuje.  
  
3.  V **Průzkumníku**, dvakrát klikněte na App.config.  
  
     Otevře se konfigurační soubor aplikace v textovém editoru.  
  
4.  Najít `<providers>` v rámci `<membership>` nebo `<roleManager>` elementu. Tyto prvky jsou podřízené objekty `<system.web>` elementu. `<membership>` Element se používá k určení zprostředkovatele ověřování a `<roleManager>` element se používá k určení zprostředkovatelů rolí.  
  
5.  Přidat `<add>` jako podřízený element `<providers>` elementu. Je nutné zadat `name` a `type` atributy, jak je znázorněno v následujícím příkladu. `type` Hodnota atributu musí být název sestavení kvalifikovaný typ. Další informace najdete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> a [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Změnit `defaultProvider` atribut `<membership>` nebo `<roleManager>` elementu, který chcete zadat název hodnota z `<add>` element, který jste přidali v předchozím kroku.  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Klientské aplikační služby](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Stránka Služby, Návrhář projektu](https://msdn.microsoft.com/library/bb398109)  
 [Dialogové okno Pokročilé nastavení služeb](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)  
 [Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [Návod: Použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Implementace zprostředkovatele členství](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Implementace zprostředkovatele rolí](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Architektura nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Vytváření a konfiguraci databázi aplikace služby systému SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
