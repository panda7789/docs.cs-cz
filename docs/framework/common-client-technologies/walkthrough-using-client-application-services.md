---
title: "Návod: Použití klientských aplikačních služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71eac85d07ac54cf15edcfcc3a86de58afef5004
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-using-client-application-services"></a>Návod: Použití klientských aplikačních služeb
Toto téma popisuje postup vytvoření aplikace Windows, která používá klientské aplikační služby k ověřování uživatelů a načítání uživatelských rolí a nastavení.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvořte aplikaci Windows Forms a použít [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Návrhář projektu povolit a nakonfigurovat klientské aplikační služby.  
  
-   Vytvořte jednoduchou aplikaci webové služby ASP.NET pro hostování aplikačních služeb a otestovat vaši konfiguraci klienta.  
  
-   Přidáte ověřování pomocí formulářů do vaší aplikace. Začněte s použitím pevně uživatelské jméno a heslo k testování služby. Potom přidáte přihlašovací formulář zadáním jako poskytovatel pověření v konfiguraci vaší aplikace.  
  
-   Přidáte funkce, které mezi sebou na základě rolí, povolení a zobrazení tlačítka pouze pro uživatele v roli "manager".  
  
-   Nastavení webového přístupu. Spustí načtením webové nastavení pro uživatele ověřeného (testovací) na **nastavení** stránky v Návrháři projektu. Návrhář formulářů Windows pak bude používat pro vazbu v textovém poli na webové nastavení. Nakonec se uložit upravený hodnota zpět na server.  
  
-   Implementujte odhlášení. Možnost odhlášení přidáte do formuláře a volání metody odhlášení.  
  
-   Povolte režim offline. Zaškrtávací políčko bude poskytovat, takže uživatelé mohou určit jejich stav připojení. Tato hodnota je pak použije k určení, zda poskytovatelů služeb aplikací klienta bude používat data místně uložená v mezipaměti ne přístup své webové služby. Když se aplikace vrátí do režimu online nakonec budou ověřovat znovu aktuálního uživatele.  
  
## <a name="prerequisites"></a>Požadavky  
 Následující součást k dokončení tohoto názorného postupu potřebujete:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Vytvoření klientské aplikace  
 První věc, kterou provedete je vytvoření projektu modelu Windows Forms. Tento návod používá Windows Forms, protože se seznámíte s ji další osoby, ale proces je podobný pro projekty Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Vytvořit klientskou aplikaci a povolit klientské aplikační služby  
  
1.  V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vyberte **soubor &#124; Nové &#124; Projekt** možnost nabídky.  
  
2.  V **nový projekt** v dialogovém **typy projektů** podokně rozbalte **jazyka Visual Basic** nebo **Visual C#** uzel a vyberte možnost **Windows** typ projektu.  
  
3.  Ujistěte se, že **rozhraní .NET Framework 3.5** vybrané, a pak vyberte možnost **formulářové aplikace Windows** šablony.  
  
4.  Změnit projekt **název** k `ClientAppServicesDemo`a potom klikněte na **OK**.  
  
     Nový projekt Windows Forms je otevřen v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
5.  Na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Návrhář projektu se zobrazí.  
  
6.  Na **služby** vyberte **povolit klientské aplikační služby**.  
  
7.  Ujistěte se, že **ověřování pomocí formulářů** nebude vybrána a poté nastavte **umístění služby ověřování**, **role služby umístění**, a **nastavení webu umístění služby** k `http://localhost:55555/AppServices`.  
  
8.  Pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]na **aplikace** nastavte **režim ověřování** k **definované aplikací**.  
  
 Návrháře ukládá nastavení zadané v souboru app.config aplikace.  
  
 V tomto okamžiku je aplikace nakonfigurovaná pro přístup k všechny tři služby ze stejného hostitele. V další části bude vytvořit hostitele jako jednoduchý aplikaci webové služby, umožňuje otestovat vaši konfiguraci klienta.  
  
## <a name="creating-the-application-services-host"></a>Vytváření hostitel aplikačních služeb  
 V této části vytvoříte jednoduchou aplikaci webové služby, která přistupuje k datům uživatele z místního souboru databáze systému SQL Server Compact. Potom bude naplnit databázi pomocí [nástroj Správa webu ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Tato jednoduchá konfigurace umožňuje rychle otestovat klientské aplikace. Jako alternativu, můžete nakonfigurovat hostitele webové služby pro přístup k datům uživatele z úplné databáze systému SQL Server nebo prostřednictvím vlastní <xref:System.Web.Security.MembershipProvider> a <xref:System.Web.Security.RoleProvider> třídy. Další informace najdete v tématu [vytváření a konfiguraci databázi aplikace služby systému SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 V následujícím postupu vytvoříte a konfigurace aplikační služby webové služby.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Vytvořit a nakonfigurovat hostitel aplikačních služeb  
  
1.  V **Průzkumníku řešení**, vyberte ClientAppServicesDemo řešení a pak na **soubor** nabídce vyberte možnost **Přidat &#124; Nový projekt**.  
  
2.  V **přidat nový projekt** dialogovém **typy projektů** podokně rozbalte položku **jazyka Visual Basic** nebo **Visual C#** uzel a vyberte možnost  **Webové** typ projektu.  
  
3.  Ujistěte se, že **rozhraní .NET Framework 3.5** vybrané, a pak vyberte možnost **aplikaci webové služby ASP.NET** šablony.  
  
4.  Změnit projekt **název** k `AppServices` a pak klikněte na **OK**.  
  
     Nový projekt aplikace ASP.NET – webové služby je k řešení přidat, a soubor Service1.asmx.vb nebo Service1.asmx.cs se zobrazí v editoru.  
  
    > [!NOTE]
    >  V tomto příkladu se nepoužívá soubor Service1.asmx.vb nebo Service1.asmx.cs. Pokud chcete zachovat prostředí pracovní přeplněná, můžete ji uzavřít a odstranit ze **Průzkumníku řešení**.  
  
5.  V **Průzkumníku řešení**, vyberte projekt aplikační služby a pak na **projektu** nabídce vyberte možnost **aplikační služby vlastnosti**.  
  
     Návrhář projektu se zobrazí.  
  
6.  Na **webové** kartě, ujistěte se, že **použít Vývojový Server sady Visual Studio** je vybrána.  
  
7.  Vyberte **specifického portu**, zadejte hodnotu `55555`a poté nastavte **virtuální cesta** k `/AppServices`.  
  
8.  Uložte všechny soubory.  
  
9. V **Průzkumníku řešení**, otevřete soubor Web.config a vyhledávat `<system.web>` počáteční značce.  
  
10. Přidejte následující značku před `<system.web>` značky.  
  
     `authenticationService`, `profileService`, A `roleService` elementů v této značek povolení a konfigurace aplikačních služeb. Při testování, `requireSSL` atribut `authenticationService` element je nastaven na hodnotu "false". `readAccessProperties` a `writeAccessProperties` atributy `profileService` element označuje, že `WebSettingsTestText` vlastnost je pro čtení a zápis.  
  
    > [!NOTE]
    >  V produkčním kódu by měla vždycky přístup ke službě ověřování, přes secure sockets layer (SSL přes protokol HTTPS). Informace o tom, jak nastavení protokolu SSL najdete v tématu [konfigurace Secure Sockets Layer (provozní příručce služby IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=91844).  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. Přidejte následující kód po `<system.web>` počáteční značce tak, aby se v rámci `<system.web>` elementu.  
  
     `profile` Element nakonfiguruje jednom webovém nastavení s názvem `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 V následujícím postupu použijete nástroj Správa webu ASP.NET k dokončení konfigurace služby a naplnit místní databázový soubor. Přidá dva uživatele s názvem `employee` a `manager` patřící do dvou rolí se stejnými názvy. Uživatelská hesla jsou `employee!` a `manager!` v uvedeném pořadí.  
  
#### <a name="to-configure-membership-and-roles"></a>Ke konfiguraci členství a rolí  
  
1.  V **Průzkumníku řešení**, vyberte projekt aplikační služby a pak na **projektu** nabídce vyberte možnost **konfigurace ASP.NET**.  
  
     **Nástroj Správa webu ASP.NET** se zobrazí.  
  
2.  Na **zabezpečení** , klikněte na **použít Průvodce nastavením zabezpečení ke konfiguraci zabezpečení krok za krokem**.  
  
     **Průvodce nastavením zabezpečení** zobrazí se **úvodní** krok.  
  
3.  Klikněte na tlačítko **Další**.  
  
     **Vyberte metodu přístupu** zobrazí krok.  
  
4.  Vyberte **z Internetu**. Tím se nakonfiguruje službu pro použití ověřování pomocí formulářů místo ověřování systému Windows.  
  
5.  Klikněte na tlačítko **Další** dvakrát.  
  
     **Definovat role** zobrazí krok.  
  
6.  Vyberte **povolit role pro tento web**.  
  
7.  Klikněte na tlačítko **Další**. **Vytvořit novou roli** se zobrazil formulář.  
  
8.  V **nový název Role** textového pole, typ `manager` a pak klikněte na **přidat roli**.  
  
     **Existující role** tabulky se zobrazí se zadanou hodnotou.  
  
9. V **nový název Role** textového pole, nahraďte `manager` s `employee` a pak klikněte na **přidat roli**.  
  
     Nová hodnota se zobrazí v **existující role** tabulky.  
  
10. Klikněte na tlačítko **Další**.  
  
     **Přidat nové uživatele** zobrazí krok.  
  
11. V **vytvořit uživatele** formuláři, zadejte následující hodnoty.  
  
  	|||  
  	|-|-|  
  	|**Uživatelské jméno**|`manager`|  
  	|**Heslo**|`manager!`|  
  	|**Potvrzení hesla**|`manager!`|  
  	|**E-mailu**|`manager@contoso.com`|  
  	|**Bezpečnostní otázku**|`manager`|  
  	|**Zabezpečení odpovědí**|`manager`|  
  
12. Klikněte na tlačítko **vytvořit uživatele**.  
  
     Zobrazí se zpráva o úspěšném provedení.  
  
    > [!NOTE]
    >  **E-mailu**, **bezpečnostní otázku**, a **bezpečnostní otázce** hodnoty jsou vyžadované formuláře, ale není použit v tomto příkladu.  
  
13. Klikněte na tlačítko **pokračovat**.  
  
     **Vytvořit uživatele** formuláři se bude zobrazovat.  
  
14. V **vytvořit uživatele** formuláři, zadejte následující hodnoty.  
  
  	|||  
  	|-|-|  
  	|**Uživatelské jméno**|`employee`|  
  	|**Heslo**|`employee!`|  
  	|**Potvrzení hesla**|`employee!`|  
  	|**E-mailu**|`employee@contoso.com`|  
  	|**Bezpečnostní otázku**|`Employee`|  
  	|**Zabezpečení odpovědí**|`employee`|  
  
15. Klikněte na tlačítko **vytvořit uživatele**.  
  
     Zobrazí se zpráva o úspěšném provedení.  
  
16. Klikněte na tlačítko **Dokončit**.  
  
     **Nástroj Správa webu** se znovu zobrazí.  
  
17. Klikněte na tlačítko **uživatele správce**.  
  
     Zobrazí se seznam uživatelů.  
  
18. Klikněte na tlačítko **upravit role** pro **zaměstnanec** uživatele a potom vyberte **zaměstnanec** role.  
  
19. Klikněte na tlačítko **upravit role** pro **manager** uživatele a potom vyberte **manager** role.  
  
20. Zavřete okno prohlížeče, který je hostitelem **nástroj Správa webu**.  
  
21. Pokud se zobrazí okno s výzvou, pokud chcete znovu načíst změněný soubor Web.config, klikněte na **Ano**.  
  
 Tím se dokončí instalace webové služby. V tomto okamžiku můžete stisknutím klávesy F5 spusťte klientské aplikace a **vývojový Server ASP.NET** se automaticky spustí společně s klientskou aplikaci. Server bude nadále spouštět po ukončení aplikace, ale se restartuje po restartování aplikace. To umožňuje zjistit všechny změny, které jste provedli do souboru Web.config.  
  
 K zastavení serveru ručně, klikněte pravým tlačítkem na ikonu vývojový Server ASP.NET v oznamovací oblasti na hlavním panelu a pak klikněte na **Zastavit**. To je užitečné příležitostně, abyste měli jistotu, že dojde k vyčištění restartování.  
  
## <a name="adding-forms-authentication"></a>Přidání ověřování pomocí formulářů  
 V následujícím postupu přidat kód pro hlavní formulář, který pokusí ověřit uživatele a odmítne přístup, když uživatel zadá neplatné přihlašovací údaje. Použijete pevně uživatelské jméno a heslo k testování služby.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>K ověření uživatele v kódu aplikace  
  
1.  V **Průzkumníku**, v projektu ClientAppServicesDemo přidat odkaz na sestavení System.Web.  
  
2.  Vyberte soubor Form1 a pak vyberte **zobrazení &#124; Kód** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hlavní nabídky.  
  
3.  V editoru kódu přidejte na začátek souboru Form1 následující příkazy.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  V **Průzkumníku**, dvakrát klikněte na Form1 zobrazíte návrháře.  
  
5.  V návrháři, klikněte dvakrát na formulář prostor pro generování <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události s názvem `Form1_Load`.  
  
     Editor kódu se zobrazí s kurzorem `Form1_Load` metoda.  
  
6.  Přidejte následující kód, který `Form1_Load` metoda.  
  
     Tento kód odepře přístup k neověřeným uživatelům ukončením aplikace. Alternativně může povolit přístup k formuláři neověřené uživatele, ale odepřít přístup k určité funkce. Za normálních okolností vám není pevný kódu uživatelské jméno a heslo jako to, ale je užitečná pro účely testování. V další části bude tento kód nahraďte robustnější kód, který se zobrazí dialogové okno přihlášení a obsahuje zpracování výjimek.  
  
     Všimněte si, že `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda je [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Tato metoda provede delegaci svou práci pro zprostředkovatele nakonfigurované ověřování a vrátí `true` Pokud je ověření úspěšné. Vaše aplikace nevyžaduje přímý odkaz na zprostředkovatele ověřování klienta.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Nyní stisknutím klávesy F5 spusťte aplikaci a vzhledem k tomu, že zadáte správné uživatelské jméno a heslo, uvidíte formulář.  
  
> [!NOTE]
>  Pokud není možné aplikaci spustit, zkuste zastavení vývojový Server ASP.NET. Po restartování serveru, ověřte, že port je nastavena na 55555.  
  
 Chcete-li místo toho zobrazí chybová zpráva, změňte <xref:System.Web.Security.Membership.ValidateUser%2A> parametry. Například nahradit druhý `"manager!"` jako parametr s nesprávné heslo `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Přidání přihlašovacího formuláře jako poskytovatel pověření  
 Můžete získat přihlašovací údaje uživatele v kódu aplikace a jejich předání <xref:System.Web.Security.Membership.ValidateUser%2A> metoda. Často je však vhodné ponechat kódu získávání přihlašovací údaje odděleně od kódu aplikace, v případě, že chcete později změnit.  
  
 V následujícím postupu nakonfigurujete aplikace použijte přihlašovací údaje poskytovatele a potom změňte vaše <xref:System.Web.Security.Membership.ValidateUser%2A> volání metody předat <xref:System.String.Empty> pro oba parametry. Signal – prázdné řetězce <xref:System.Web.Security.Membership.ValidateUser%2A> metoda k volání <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metoda zprostředkovatele nakonfigurovali přihlašovací údaje.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Ke konfiguraci vaší aplikace pro použití poskytovatele přihlašovacích údajů  
  
1.  V **Průzkumníku řešení**, vyberte ClientAppServicesDemo projekt a pak na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Návrhář projektu se zobrazí.  
  
2.  Na **služby** nastavte **volitelné: Poskytovatel pověření** následující hodnotu. Tato hodnota určuje název sestavení kvalifikovaný typu.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  V souboru Form1, nahraďte kód v `Form1_Load` metoda následujícím kódem.  
  
     Tento kód zobrazí uvítací zprávu a pak zavolá `ValidateUsingCredentialsProvider` metoda, která přidáte v dalším kroku. Pokud není uživatel ověřen, `ValidateUsingCredentialsProvider` metoda vrátí `false` a `Form1_Load` metoda vrátí. Žádný další kód zabrání spuštění před aplikací ukončí. Zobrazení uvítací zprávy je užitečné, aby bylo jasné, když se aplikace restartuje. Přidáte kód při implementaci odhlášení dále v tomto návodu aplikaci restartovat.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Přidejte následující metodu po `Form1_Load` metoda.  
  
     Tato metoda předá prázdné řetězce `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda, což způsobí, že se objeví dialogové okno přihlásit. Pokud není k dispozici, službu ověřování <xref:System.Web.Security.Membership.ValidateUser%2A> vyvolá metoda výjimku <xref:System.Net.WebException>. V takovém případě `ValidateUsingCredentialsProvider` metoda zobrazí zprávu upozornění a požádá, pokud uživatel chce a zkuste to znovu v režimu offline. Tato funkce vyžaduje **uložit hodnoty hash hesla místně pro povolení offline přihlášení** funkce popsané v [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Tato funkce je povolená ve výchozím nastavení pro nové projekty.  
  
     Pokud uživatel není ověřen, `ValidateUsingCredentialsProvider` metoda zobrazí chybovou zprávu a ukončí aplikaci. Nakonec tato metoda vrací výsledek pokusu o ověření.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Vytváření přihlašovací formulář  
 Přihlašovací údaje poskytovatele je třída, která implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. Toto rozhraní obsahuje jedinou metodu s názvem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> , který vrací <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> objektu. Následující postupy popisují, jak vytvořit dialogové okno přihlášení, který implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> zobrazení samotného a vrátíte se přihlašovací údaje zadané uživatelem.  
  
 Samostatné procedury jsou uvedeny pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] C# a protože [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] poskytuje **přihlašovací formulář** šablony. To umožňuje ušetřit nějaký čas a úsilí kódování.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Chcete-li vytvořit dialogové okno přihlášení jako poskytovatel pověření v jazyce Visual Basic  
  
1.  V **Průzkumníku řešení**, vyberte ClientAppServicesDemo projekt a pak na **projektu** nabídce vyberte možnost **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **přihlašovací formulář** šablony, změňte položku **název** k `Login.vb`a potom klikněte na **přidat** .  
  
     Dialogové okno přihlášení se zobrazí v Návrháři formulářů Windows.  
  
3.  V návrháři, vyberte **OK** tlačítko a pak na **vlastnosti** nastavte `DialogResult` k `OK`.  
  
4.  V návrháři, přidejte `CheckBox` ovládacího prvku formuláře v části **heslo** textové pole.  
  
5.  V **vlastnosti** okno, zadejte **(název)** hodnotu `rememberMeCheckBox` a **Text** hodnotu `&Remember me`.  
  
6.  Vyberte **zobrazení &#124; Kód** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hlavní nabídky.  
  
7.  V editoru kódu přidejte následující kód do horní části souboru.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Upravte podpis třídy tak, aby třída implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Ujistěte se, že kurzor je po `IClientformsAuthenticationCredentialsProvider`, a stiskněte klávesu ENTER pro generování `GetCredentials` metoda.  
  
10. Vyhledejte <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementace a nahraďte ji následujícím kódem.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Následující postup C# poskytuje celý kód výpis pro dialogové okno jednoduchého přihlášení. Rozložení pro tohoto dialogového okna je trochu hrubých, ale je důležitou součástí <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementace.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Chcete-li vytvořit dialogové okno přihlášení jako poskytovatel pověření v jazyce C#  
  
1.  V **Průzkumníku řešení**, vyberte ClientAppServicesDemo projekt a pak na **projektu** nabídce vyberte možnost **přidat třídu**.  
  
2.  V **přidat novou položku** dialogové okno, změny **název** k `Login.cs`a potom klikněte na **přidat**.  
  
     Login.cs soubor se otevře v editoru kódu.  
  
3.  Ve výchozím kódu nahraďte následujícím kódem.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Teď můžete aplikaci spustit a zobrazit dialogové okno přihlášení zobrazí. Pokud chcete vyzkoušet tento kód, zkuste jiné přihlašovací údaje platné a neplatná a potvrďte, že máte přístup formulář pouze s platné přihlašovací údaje. Platná uživatelská jména jsou `employee` a `manager` s hesly `employee!` a `manager!` v uvedeném pořadí.  
  
> [!NOTE]
>  Nevybírejte **Zapamatovat uživatele** tohoto bodu nebo nebude možné se přihlásit jako jiný uživatel, dokud neimplementujete odhlášení dále v tomto návodu.  
  
## <a name="adding-role-based-functionality"></a>Přidání funkce na základě rolí  
 V následujícím postupu přidání tlačítka do formuláře a zobrazit ji pouze pro uživatele v roli správce.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Chcete-li změnit uživatelského rozhraní na základě role uživatele  
  
1.  V **Průzkumníku řešení**v projektu ClientAppServicesDemo vyberte Form1 a pak vyberte **zobrazení &#124; Návrhář** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hlavní nabídky.  
  
2.  V návrháři, přidejte <xref:System.Windows.Forms.Button> ovládacího prvku formuláře z **sada nástrojů**.  
  
3.  V **vlastnosti** nastavte následující vlastnosti pro tlačítko.  
  
  	|Vlastnost|Hodnota|  
  	|--------------|-----------|  
  	|**(Name)**|managerOnlyButton|  
  	|**Text**|& úkol Správce úloh|  
  	|**Viditelné**|`False`|  
  
4.  V editoru kódu pro Form1 přidejte následující kód do konce `Form1_Load` metoda.  
  
     Tento kód zavolá `DisplayButtonForManagerRole` metoda, která přidáte v dalším kroku.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Přidejte následující metodu za účelem Form1 třídy.  
  
     Tato metoda volá <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metodu <xref:System.Security.Principal.IPrincipal> vrácený `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost. U aplikací nakonfigurovaný na použití klientských aplikačních služeb, vrátí tato vlastnost <xref:System.Web.ClientServices.ClientRolePrincipal>. Vzhledem k tomu, že tato třída implementuje <xref:System.Security.Principal.IPrincipal> rozhraní, není nutné explicitně na něj odkazovat.  
  
     Pokud je uživatel v roli "manager" `DisplayButtonForManagerRole` metoda nastaví <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `managerOnlyButton` k `true`. Tato metoda také zobrazí chybovou zprávu, pokud <xref:System.Net.WebException> je vyvolána, což naznačuje, zda je služba role není k dispozici.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Metoda vždy vrátí `false` Pokud vypršela platnost přihlášení uživatele. Tím nedojde, pokud aplikace zavolá <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metoda jednou krátce po ověření, jak je znázorněno v příkladu kódu pro účely tohoto postupu. Pokud vaše aplikace musí získat role uživatele v jinou dobu, můžete chtít přidejte kód, který znovu ověřit uživatele, jehož přihlášení vypršela. Pokud všechny platné uživatele přiřazené k rolím, můžete určit, zda přihlášení vypršela platnost voláním <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> metoda. Pokud jsou vráceny žádné role, přihlášení vypršela platnost. Příklad této funkce, najdete v článku <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> metoda. Tato funkce je nutné, pokud jste vybrali pouze **vyžadovat, aby se znovu přihlaste vždy, když vyprší platnost souboru cookie serveru uživatelé** v konfiguraci vaší aplikace. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Pokud je ověření úspěšné, nastaví zprostředkovatele ověřování klienta <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost, která má instance <xref:System.Web.ClientServices.ClientRolePrincipal> třídy. Tato třída implementuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metoda tak, aby práce se deleguje na poskytovateli nakonfigurované role. Jako dříve, kód aplikace nevyžaduje přímý odkaz na poskytovatele služeb.  
  
 Teď můžete aplikaci spustit a přihlaste se jako zaměstnanec zda tlačítko není objeví, a pak se přihlaste jako správce, aby tlačítko zobrazit.  
  
## <a name="accessing-web-settings"></a>Přístup k webové nastavení  
 V následujícím postupu přidat textové pole formuláře a navázat jej na webové nastavení. Jako předchozí kód, který používá ověřování a rolí nastavení kódu není přístup k poskytovateli nastavení přímo. Místo toho použije silného typu `Settings` – třída (přístup jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) vygenerovat pro váš projekt pomocí [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Pokud chcete použít nastavení webové uživatelské rozhraní  
  
1.  Ujistěte se, že **vývojový Server ASP.NET Web** je stále spuštěná kontrolou oznamovací oblasti na hlavním panelu. Pokud server, je nutné zastavit, restartovat aplikaci (které se automaticky spustí server) potom zavřete dialogové okno přihlášení.  
  
2.  V **Průzkumníku řešení**, vyberte ClientAppServicesDemo projekt a pak na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Návrhář projektu se zobrazí.  
  
3.  Na **nastavení** , klikněte na **nastavení webové zatížení**.  
  
     A **přihlášení** zobrazí se dialogové okno.  
  
4.  Zadejte přihlašovací údaje pro zaměstnance nebo správce a klikněte na tlačítko **protokolu v**. Webové nastavení použijete je nakonfigurovaný pro přístup podle pouze ověřené uživatele, kliknutím na **přihlášení přeskočit** nenačte všechna nastavení.  
  
     `WebSettingsTestText` Nastavení se zobrazí v návrháři se výchozí hodnota `DefaultText`. Kromě toho `Settings` třídu, která obsahuje `WebSettingsTestText` vlastnost je generován pro projekt.  
  
5.  V **Průzkumníku řešení**v projektu ClientAppServicesDemo vyberte Form1 a pak vyberte **zobrazení &#124; Návrhář** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hlavní nabídky.  
  
6.  V návrháři, přidejte <xref:System.Windows.Forms.TextBox> ovládacího prvku do formuláře.  
  
7.  V **vlastnosti** okno, zadejte **(název)** hodnotu `webSettingsTestTextBox`.  
  
8.  V editoru kódu, přidejte následující kód do konce `Form1_Load` metoda.  
  
     Tento kód zavolá `BindWebSettingsTestTextBox` metoda, která přidáte v dalším kroku.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Přidejte následující metodu za účelem Form1 třídy.  
  
     Tato metoda vytvoří vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost `webSettingsTestTextBox` k `WebSettingsTestText` vlastnost `Settings` třídy vytvořené dříve v tomto postupu. Tato metoda také zobrazí chybovou zprávu, pokud <xref:System.Net.WebException> je vyvolána výjimka, která označuje, že je nastavení webové služby není k dispozici.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Datová vazba obvykle využije k povolení automatického obousměrnou komunikaci mezi ovládacího prvku a webové nastavení. Můžete však také přístup nastavení webové přímo jako uvedené v následujícím příkladu:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. V návrháři, vyberte formulář a pak na **vlastnosti** okně klikněte na tlačítko **události** tlačítko.  
  
11. Vyberte <xref:System.Windows.Forms.Form.FormClosing> událost a potom stiskněte klávesu ENTER pro vygenerování obslužné rutiny.  
  
12. Vygenerovaný metoda nahraďte následujícím kódem.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Volání obslužné rutiny událostí `SaveSettings` metodu, která se používá také odhlášení funkce, které budete přidávat v další části. `SaveSettings` Metoda nejdřív potvrdí, že uživatel nezaznamenal. Dělá to kontrolou <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> vlastnost <xref:System.Security.Principal.IIdentity> vrácený aktuální objekt zabezpečení. Aktuální objekt zabezpečení se načítají prostřednictvím `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> vlastnost. Pokud uživatel byl ověřen pro klientské aplikační služby, typ ověřování, který bude "ClientForms". `SaveSettings` Metoda právě nelze zkontrolovat <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> vlastnost vzhledem k tomu, že uživatel může mít platnou identitu systému Windows po odhlášení.  
  
     Pokud uživatel nezaznamenal out `SaveSettings` volání metod <xref:System.Configuration.ApplicationSettingsBase.Save%2A> metodu `Settings` třídy vytvořené dříve v tomto postupu. Tuto metodu můžete vyvolat <xref:System.Net.WebException> Pokud vypršela platnost souboru cookie pro ověřování. K tomu dojde pouze v případě, že jste vybrali **vyžadovat, aby se znovu přihlaste vždy, když vyprší platnost souboru cookie serveru uživatelé** v konfiguraci vaší aplikace. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Metoda zpracovává vypršení platnosti souboru cookie voláním <xref:System.Web.Security.Membership.ValidateUser%2A> zobrazíte dialogové okno přihlášení. Pokud uživatel úspěšně přihlásí, `SaveSettings` metoda se pokusí znovu uložit nastavení voláním sebe sama.  
  
     Jako v předchozí kód `SaveSettings` metoda zobrazí chybovou zprávu, pokud Vzdálená služba není k dispozici. Pokud poskytovatel nastavení nemají přístup k vzdálené služby, jsou stále nastavení uložit do místní mezipaměti a znovu po restartování aplikace.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Přidejte následující metodu za účelem Form1 třídy.  
  
     Tento kód zpracovává <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> událostí a zobrazí upozornění, pokud některé z nastavení nelze uložit. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Události nedojde, pokud nastavení služby není k dispozici nebo pokud vypršela platnost souboru cookie pro ověřování. Jeden příklad, kdy <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> události dojde, je, pokud se uživatel přihlásí již. Můžete otestovat této obslužné rutiny události přidáním odhlášení kódu `SaveSettings` metody přímo před <xref:System.Configuration.ApplicationSettingsBase.Save%2A> volání metody. Odhlášení kód, který můžete použít, je popsaná v další části.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Pro jazyk C#, přidejte následující kód do konce `Form1_Load` metoda. Tento kód přidruží metoda, kterou jste přidali v posledním kroku s <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> událostí.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 K testování aplikace v tomto okamžiku spustit několikrát jako zaměstnanců a správce a zadejte jiné hodnoty do textového pole. Hodnoty se zachová napříč relacemi na jednotlivé uživatele.  
  
## <a name="implementing-logout"></a>Implementace odhlášení  
 Když uživatel vybere **Zapamatovat uživatele** políčko při přihlášení, aplikace nebude automaticky ověření uživatele při dalším spuštění. Automatické ověření bude pokračovat, pak během aplikace je v režimu offline, nebo do vypršení platnosti souboru cookie pro ověřování. V některých případech ale více uživatelé budou potřebovat přístup k aplikaci nebo jednoho uživatele může občas přihlásit se přes různé přihlašovací údaje. Pokud chcete povolit tento scénář, musí implementovat funkce odhlášení, jak je popsáno v následujícím postupu.  
  
#### <a name="to-implement-logout-functionality"></a>K implementaci odhlášení funkcí  
  
1.  V Návrháři Form1 přidat <xref:System.Windows.Forms.Button> ovládacího prvku formuláře z **sada nástrojů**.  
  
2.  V **vlastnosti** okno, zadejte **(název)** hodnotu `logoutButton` a **Text** hodnotu **& Odhlásit**.  
  
3.  Dvakrát klikněte `logoutButton` ke generování <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     Editor kódu se zobrazí s kurzorem `logoutButton_Click` metoda.  
  
4.  Nahraďte vygenerovaného `logoutButton_Click` metoda následujícím kódem.  
  
     První volání této obslužné rutiny události `SaveSettings` metoda, kterou jste přidali v předchozí části. Potom volání obslužné rutiny události <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> metoda. Pokud není k dispozici, službu ověřování <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> vyvolá metoda výjimku <xref:System.Net.WebException>. V takovém případě `logoutButton_Click` metoda zobrazí zprávu upozornění a dočasně přepne do režimu offline na odhlášení uživatele. Offline režimu je popsaná v další části.  
  
     Odhlášení odstraní místní ověřovacího souboru cookie, že přihlášení se bude vyžadovat, když se aplikace restartuje. Po odhlášení obslužné rutiny události restartování aplikace. Po restartování aplikace zobrazí zobrazení uvítací zprávy dialogové okno přihlášení. Zobrazení uvítací zprávy umožňuje vymazat, restartování aplikace. Tím zabráníte nejasnostem, pokud uživatel musí přihlásit se uložit nastavení a pak musí přihlásit znovu protože restartování aplikace.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 K testování funkčnosti odhlášení, spusťte aplikaci a vyberte **Zapamatovat uživatele** v dialogovém okně přihlášení. Potom zavřete a restartujte aplikaci potvrďte, že už máte k přihlášení. Nakonec znovu spusťte aplikaci kliknutím při odhlášení.  
  
## <a name="enabling-offline-mode"></a>Povolení režimu Offline  
 V následujícím postupu přidat zaškrtávací políčko pro formulář umožňující uživateli zadat offline režimu. Aplikace označuje offline režimu nastavením `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> vlastnost `true`. V režimu offline je uložený na místní pevný disk v umístění indikován <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> vlastnost. To znamená, že je v režimu offline uložený na jednotlivých uživatelů, každou aplikaci.  
  
 V offline režimu všechny požadavky aplikace služby načtení dat z místní mezipaměti namísto pokusu o přístup ke službám. Ve výchozí konfiguraci místní data zahrnují šifrovaném formátu hesla uživatele. To umožňuje uživateli přihlásit se při aplikace je v offline režimu. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Chcete-li povolit offline režimu v aplikaci  
  
1.  V **Průzkumníku řešení**v projektu ClientAppServicesDemo vyberte Form1 a pak vyberte **zobrazení &#124; Návrhář** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hlavní nabídky.  
  
2.  V návrháři, přidejte <xref:System.Windows.Forms.CheckBox> ovládacího prvku do formuláře.  
  
3.  V **vlastnosti** okno, zadejte **(název)** hodnotu `workOfflineCheckBox` a **Text** hodnotu **& pracovní offline**.  
  
4.  V **vlastnosti** okně klikněte **události** tlačítko.  
  
5.  Vyberte <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost a potom stiskněte klávesu ENTER pro vygenerování obslužné rutiny.  
  
6.  Vygenerovaný metoda nahraďte následujícím kódem.  
  
     Tento kód aktualizace <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> hodnotu a bezobslužně revalidates uživatele, když se vrátí do režimu online. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> Metoda použije pověření uložená v mezipaměti, takže není nutné explicitně přihlášení uživatele. Pokud ověřovací služby není k dispozici, zobrazí se zpráva upozornění a aplikace zůstává v režimu offline.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Metoda je pouze ke zvýšení pohodlí. Protože nemá návratovou hodnotu, nelze to označuje, zda opětovné ověření se nezdařilo. Opětovné ověření může selhat, například pokud přihlašovací údaje uživatele se změnila na serveru. V takovém případě můžete chtít obsahovat kód, který explicitně ověřuje uživatele po volání služby selže. Další informace najdete v části Nastavení webového přístupu k dříve v tomto návodu.  
  
     Po opětovné ověření, tento kód uloží změny do místní nastavení webové voláním `SaveSettings` metoda, kterou jste přidali dříve. Potom načte žádné nové hodnoty na serveru při volání <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> metoda projektu `Settings` – třída (přístup jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Přidejte následující kód do konce `Form1_Load` metoda a ujistěte se, že políčko zobrazuje aktuální stav připojení.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Tím dokončíte ukázková aplikace. Chcete-li otestovat v režimu offline, spusťte aplikaci, přihlaste se jako zaměstnanců nebo správce a pak vyberte **práce offline**. Změňte hodnotu v textovém poli a pak zavřete aplikaci. Restartování aplikace. Předtím, než se přihlásíte, klikněte pravým tlačítkem na ikonu vývojový Server ASP.NET v oznamovací oblasti na hlavním panelu a pak klikněte na **Zastavit**. Přihlaste se pak jako normální. I když server není spuštěn, můžete stále přihlásit. Upravte hodnotu textového pole, ukončení a restartování a zobrazit tak upravené hodnotu.  
  
## <a name="summary"></a>Souhrn  
 V tomto návodu jste zjistili, jak povolit a používat klientské aplikační služby v aplikaci Windows Forms. Po nastavení testovací server, přidat kód do aplikace k ověření uživatelů a rolí uživatele a nastavení aplikací ze serveru načíst. Také jste zjistili, jak povolit offline režimu, aby vaše aplikace používá místní data mezipaměti místo vzdálené služby, pokud připojení není k dispozici.  
  
## <a name="next-steps"></a>Další kroky  
 V reálné aplikaci bude přístup k datům pro mnoho uživatelů ze vzdáleného serveru, který nemusí být vždy k dispozici, nebo může přejděte bez předchozího upozornění. Chcete-li aplikace robustní, musí použít odpovědět správně na situace, kdy služba není k dispozici. Tento názorný postup obsahuje bloků try/catch k zachycení <xref:System.Net.WebException> a zobrazí se chybová zpráva, pokud služba není k dispozici. V produkčním kódu můžete chtít zpracovávat tento případ přepnout do režimu offline, ukončení aplikace nebo odepření přístupu ke konkrétním funkcím.  
  
 Pokud chcete zvýšit zabezpečení aplikace, zajistěte, aby důkladně otestovat aplikace a server před nasazením.  
  
## <a name="see-also"></a>Viz také  
 [Klientské aplikační služby](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Nástroj Správa webu ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Vytváření a konfiguraci databázi aplikace služby systému SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [Návod: Použití aplikačními službami ASP.NET](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
