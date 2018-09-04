---
title: 'Postupy: Konfigurace klientských aplikačních služeb'
ms.date: 03/30/2017
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
ms.openlocfilehash: a65c216397f240b77eb81f88d8f2a2da122e1ccf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560675"
---
# <a name="how-to-configure-client-application-services"></a>Postupy: Konfigurace klientských aplikačních služeb
Toto téma popisuje, jak pomocí sady Visual Studio **Návrháře projektu** povolení a konfigurace klientských aplikačních služeb. Klientské aplikační služby můžete použít k ověření uživatelů a načíst role uživatele a nastavení z existující [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační službu. Po konfiguraci, můžete přístup povolené služby v kódu aplikace, jak je popsáno v [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Další informace o [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační služby, najdete v článku [přehled aplikačních služeb ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Můžete povolit a nakonfigurovat klientské aplikační služby na **služby** stránku **Návrháře projektu**. **Služby** stránka aktualizuje hodnoty v souboru App.config vašeho projektu. Pro přístup k **Návrháře projektu**, použijte **vlastnosti** příkaz **projektu** nabídky. Další informace o **služby** stránky, přečtěte si téma [stránka služby, Návrhář projektu](https://msdn.microsoft.com/library/bb398109).  
  
 Následující postup popisuje, jak provést základní konfiguraci pro klientské aplikační služby. Pokročilá konfigurace, které možnosti jsou popsané v předchozích částech.  
  
### <a name="to-configure-client-application-services"></a>Konfigurace klientských aplikačních služeb  
  
1.  V **Průzkumníka řešení**, vyberte uzel projektu a pak na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     **Návrháře projektu** se zobrazí.  
  
2.  Klikněte na tlačítko **služby** kartu. **Služby** stránky se zobrazí, jak je znázorněno na následujícím obrázku.  
  
     ![Na kartě služeb v Návrháři projektu](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Na **služby** stránce **povolit klientské aplikační služby**.  
  
    > [!NOTE]
    >  Klientské aplikační služby vyžadují plnou verzi rozhraní .NET Framework a nejsou podporovány v rozhraní .NET Framework Client Profile. Pokud **povolit klientské aplikační služby** zaškrtávací políčko je zakázaná. Ověřte, zda **Cílová architektura** je nastavená na rozhraní .NET Framework 3.5 nebo novější. Chcete-li zobrazit **Cílová architektura** nastavení v jazyce C#, otevřete Návrhář projektu a pak klikněte na tlačítko **aplikace** stránky. Chcete-li zobrazit **Cílová architektura** nastavení v jazyce Visual Basic, otevřete Návrhář projektu, klikněte na tlačítko **kompilaci** stránce a potom klikněte na **Upřesnit možnosti kompilace**.  
  
4.  Vyberte **použít ověřování pomocí formulářů** Pokud budete chtít poskytnout ovládacími prvky pro přihlášení nebo dialogové okno, nebo vyberte **ověřování pomocí Windows** používat identitu poskytnutou v operačním systému. Další informace najdete v tématu [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Pokud vyberete **ověřování pomocí Windows**, klientské aplikační služby, se automaticky nakonfigurují pro použití jiné databáze systému SQL Server Compact. To je uvedeno v **pokročilé nastavení služeb** dialogovému oknu, jak je popsáno v další části. Pokud pak vyberete **použít ověřování pomocí formulářů**, **použít vlastní připojovací řetězec** nastavení nebude automaticky vymazána. To může vést k chybám Pokud [!INCLUDE[ssEW](../../../includes/ssew-md.md)] databáze již byla vygenerována pro použití s ověřováním Windows. Chcete-li tyto chyby opravit, zrušte **použít vlastní připojovací řetězec** nastavení **pokročilé nastavení služeb** dialogové okno.  
  
5.  Pokud jste vybrali **použít ověřování pomocí formulářů**v **umístění služby ověřování** pole, zadejte adresu URL hostitele služby, bez zahrnutí názvu souboru. Návrhář automaticky připojí standardní název_souboru (Authentication_JSON_AppService.axd), když zapíše hodnoty do konfiguračního souboru.  
  
6.  Případně pokud jste vybrali **použít ověřování pomocí formulářů**, můžete zadat hodnotu v **poskytovatele přihlašovacích údajů** pole. Přihlašovací údaje poskytovatel musí implementovat <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. S použitím poskytovatele přihlašovacích údajů, můžete oddělit přihlášení uživatelského rozhraní od jiného kódu aplikací. To umožňuje vytvořit dialogové okno podporou jediného přihlášení pro použití ve více aplikacích. Další informace najdete v tématu [postupy: implementace přihlášení uživatele u klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Pokud chcete zadat poskytovatele přihlašovacích údajů, je nutné zadat jako název typu kvalifikovaného pro sestavení. Další informace najdete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> a [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md). Ve své nejjednodušší podobě vypadá podobně jako v následujícím příkladu představuje název typu kvalifikovaného pro sestavení:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  V **umístění služby role** a **nastavení webové služby umístění** textová pole, zadejte umístění služby pro jednotlivé služby bez zahrnutí názvu souboru. Návrhář automaticky připojí názvy standardních souborů (Role_JSON_AppService.axd a Profile_JSON_AppService.axd) při zapíše hodnoty do konfiguračního souboru.  
  
8.  Případně můžete kliknout **Upřesnit** Změnit pokročilé nastavení, jako je například místní chování ukládání do mezipaměti. Další informace najdete v dalším postupu.  
  
## <a name="advanced-configuration"></a>Pokročilá konfigurace  
 Následující postupy popisují postup konfigurace klientských aplikačních služeb pro méně běžné scénáře. Například můžete použít tyto možnosti konfigurace pro aplikace nasazené na veřejných místech, nebo chcete použít jako mezipaměť místních dat databázi systému SQL Server Compact šifrované.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Postup při konfiguraci rozšířených nastavení pro klientské aplikační služby  
  
1.  Na **služby** stránku **Návrháře projektu**, klikněte na tlačítko **Upřesnit**.  
  
     **Pokročilé nastavení služeb** dialogové okno se zobrazí, jak je znázorněno na následujícím obrázku. Další informace o tomto dialogovém najdete v tématu [rozšířená nastavení pro dialogové okno služby](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Upřesňující nastavení pro dialogové okno služby](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Zaškrtněte nebo zrušte zaškrtnutí **uložit hodnoty hash hesla místně umožňující přihlášení offline**. Pokud vyberete tuto možnost, zašifrované heslo uživatele se do mezipaměti místně. To je užitečné, pokud se rozhodnete implementovat pro vaši aplikaci v režimu offline režimu. Tato možnost aktivní, můžete ověřit uživatele i v případě <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> je nastavená vlastnost `true`.  
  
3.  Zaškrtněte nebo zrušte zaškrtnutí **vyžadují, aby uživatelé přihlásit znovu pokaždé, když vyprší platnost souboru cookie server**. Ověřovacího souboru cookie je nakonfigurovaná na vzdálenou službu a určuje, jak dlouho zůstane aktivní přihlášení uživatele. Další informace o tom, jak nakonfigurovat soubor cookie, najdete v článku `timeout` atribut [tvoří prvek pro ověřování (schéma nastavení technologie ASP.NET)](https://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Pokud vyberete tuto možnost, při pokusu o přístup k vzdálené role nebo vyvolá výjimku webové nastavení služby po vypršení platnosti souboru cookie pro ověřování <xref:System.Net.WebException>. Můžete zpracovat tuto výjimku a zobrazit dialogové okno přihlášení pro uživatele znovu ověřit. Příklad toto chování najdete v tématu [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Tato možnost je užitečná pro aplikace nasazené na veřejných místech, abyste měli jistotu, že uživatelé, kteří neustále spuštěný aplikace po použití zůstat ověření po neomezenou dobu.  
  
     Pokud zrušíte zaškrtnutí této možnosti a pokus o přístup k vzdálené služby po vypršení platnosti souboru cookie pro ověřování, bude automaticky ověřit uživatele.  
  
4.  Zadejte hodnotu pro **časový limit mezipaměti služby Role**. Nastavte tento časový interval na malou hodnotu při aktualizaci role často nebo větší hodnotu při aktualizaci role zřídka. Pokud se rozhodnete implementovat offline režimu, nastavte časový interval velké hodnoty, aby se zabránilo informace o rolích z vypršení platnosti aplikace je offline.  
  
     Zprostředkovatel rolí má přístup k hodnoty uložené v mezipaměti role nebo služby role při volání <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Chcete-li programově resetování mezipaměti a vynutit tato metoda pro přístup k vzdálené službě, zavolejte <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.  
  
5.  Zaškrtněte nebo zrušte zaškrtnutí **použít vlastní připojovací řetězec**. Další informace najdete v dalším postupu.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>Konfigurace klientských aplikačních služeb pro použití jiné databáze pro místní mezipaměti  
  
1.  Na **služby** stránku **Návrháře projektu**, klikněte na tlačítko **Upřesnit**.  
  
     **Pokročilé nastavení služeb** zobrazí se dialogové okno.  
  
2.  Vyberte **použít vlastní připojovací řetězec**.  
  
     Výchozí hodnota `Data Source = |SQL/CE|` se zobrazí v textovém poli.  
  
3.  Pro vygenerování a použití databáze SQL Server Compact, ponechte výchozí hodnotu řetězce připojení. Visual Studio bude generovat soubor databáze a vložit ho do adresáře indikován <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> vlastnost.  
  
4.  Pro vygenerování a použití šifrované [!INCLUDE[ssEW](../../../includes/ssew-md.md)] databáze, přidejte `password` a `encrypt database` hodnoty na připojovací řetězec, jak je znázorněno v následujícím příkladu.  
  
    > [!NOTE]
    >  Nezapomeňte zadat silné heslo. Heslo nelze změnit po vygenerování databáze.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Použití databáze SQL serveru, zadejte připojovací řetězec. Informace o formátech platný připojovací řetězec najdete v dokumentaci k SQL serveru. Tato databáze není generován automaticky. Připojovací řetězec musí odkazovat na existující databázi, která můžete vytvořit pomocí následujících příkazů SQL.  
  
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
  
## <a name="using-custom-providers"></a>Pomocí vlastního zprostředkovatele  
 Ve výchozím nastavení, funkce klienta aplikace služby používá zprostředkovatele v <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> oboru názvů. Při konfiguraci vaší aplikace pomocí **služby** stránku **Návrháře projektu**, odkazy na tyto poskytovatelé jsou přidány do souboru App.config. Tito poskytovatelé výchozí přístup k odpovídající zprostředkovatele na serveru. Webové služby jsou často nakonfigurovaný přístup k uživatelským datům prostřednictvím poskytovatelů, jako <xref:System.Web.Security.SqlMembershipProvider> a <xref:System.Web.Security.SqlRoleProvider>.  
  
 Pokud chcete použít vlastní poskytovatelé, bude obvykle změnit zprostředkovatele na straně serveru, tak, aby ovlivňují všechny klientské aplikace, které přistupují k serveru. Ale máte možnost použití jiného než výchozího zprostředkovatele na straně klienta. Vlastní zprostředkovatelé ověřování nebo role v souboru App.config vašeho projektu, můžete určit, jak je znázorněno v následujícím postupu. Informace o tom, jak vytvořit vlastní ověřování a zprostředkovatele rolí najdete v tématu [implementace zprostředkovatele členství](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) a [implementaci zprostředkovatele rolí](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Můžete použít také vlastních nastavení zprostředkovatele úpravou váš projekt `Settings` třídy (přistupuje jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v jazyce Visual Basic). Další informace najdete v tématu [architektura nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>Konfigurace klientských aplikačních služeb použít jiné než výchozí poskytovatele  
  
1.  Pokud chcete použít jiné než výchozí ověřování nebo poskytovatel služeb rolí, nejdřív dokončit všechna ostatní nastavení konfigurace s použitím **služby** stránky.  
  
2.  Zavřít **Návrhář projektu**. To je nezbytné, protože **služby** stránka automaticky aktualizuje soubor App.config i v případě, že všechna nastavení neprovádějte žádné změny. Pokud jste ručně upravit soubor App.config, jak je popsáno v tomto postupu a pak se vraťte k **služby** stránku, provedené změny se resetuje.  
  
3.  V **Průzkumníka řešení**, dvakrát klikněte na panel App.config.  
  
     Konfigurační soubor aplikace se otevře v textovém editoru.  
  
4.  Najít `<providers>` element v rámci `<membership>` nebo `<roleManager>` elementu. Tyto prvky jsou podřízených objektů `<system.web>` elementu. `<membership>` Element slouží k určení zprostředkovatele ověřování a `<roleManager>` element slouží k určení zprostředkovatele rolí.  
  
5.  Přidat `<add>` element jako podřízený objekt `<providers>` elementu. Je nutné zadat `name` a `type` atributy, jak je znázorněno v následujícím příkladu. `type` Hodnota atributu musí být s názvem typu kvalifikovaného pro sestavení. Další informace najdete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> a [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Upravit `defaultProvider` atribut `<membership>` nebo `<roleManager>` prvku zadejte hodnotu názvu ze `<add>` element, který jste přidali v předchozím kroku.  
  
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
 [Implementace zprostředkovatele členství](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Implementace zprostředkovatele rolí](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Architektura nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Vytváření a konfiguraci této databáze systému SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
