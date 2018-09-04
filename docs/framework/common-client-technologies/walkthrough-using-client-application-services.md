---
title: 'Návod: Použití klientských aplikačních služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
ms.openlocfilehash: b800848fc3cefb1f82fb5822007bc670c1684363
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539889"
---
# <a name="walkthrough-using-client-application-services"></a>Návod: Použití klientských aplikačních služeb
Toto téma popisuje, jak vytvořit aplikaci Windows, která používá k ověřování uživatelů a získání role uživatele a nastavení klientských aplikačních služeb.  
  
 V tomto podrobném návodu můžete provádět následující úlohy:  
  
-   Vytvoření aplikace modelu Windows Forms a použití Návrháře projektu sady Visual Studio k povolení a konfigurace klientských aplikačních služeb.  
  
-   Vytvoření jednoduché aplikace webové služby ASP.NET pro hostování aplikačních služeb a testování konfigurace klienta.  
  
-   Přidání ověřování pomocí formulářů pro aplikaci. Začněte s použitím pevně zakódované uživatelské jméno a heslo k otestování služby. Potom přidáte přihlašovací formulář tak, že zadáte jako přihlašovací údaje poskytovatele v konfiguraci vaší aplikace.  
  
-   Doplňují na základě rolí, povolení a zobrazení tlačítka pouze pro uživatele v roli "správce".  
  
-   Nastavení webového přístupu. Začnete načtením nastavení webu pro uživatele ověřeného (testovací) na **nastavení** stránky Návrháře projektu. Návrhář formulářů Windows pak bude používat k vytvoření vazby textové pole webovém nastavení. Nakonec se uloží upravené hodnoty se serverem.  
  
-   Implementace odhlašování. Možnost odhlásit přidáte do formuláře a volání metody pro odhlášení.  
  
-   Povolte režim offline. Zaškrtávací políčko bude poskytovat tak, aby uživatelé můžou zadat jejich stav připojení. Pak použijete tuto hodnotu určující, zda poskytovatelů služeb aplikací klienta bude dat místně uložených v mezipaměti namísto přístup ke své webové služby. Když se aplikace vrátí do režimu online nakonec bude ověřovat znovu aktuálního uživatele.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty k dokončení tohoto návodu:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Vytvoření klientské aplikace  
 První věc, která bude provádět, je vytvoření projektu Windows Forms. Tento návod používá Windows Forms, protože se seznámíte s ním více lidí, ale proces se podobá pro projekty Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Vytvořit klientskou aplikaci a povolit klientské aplikační služby  
  
1.  V sadě Visual Studio, vyberte **souboru &#124; nový &#124; projektu** nabídky.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokně rozbalte **jazyka Visual Basic** nebo **Visual C#** uzel a vyberte **Windows** typ projektu.  
  
3.  Ujistěte se, že **rozhraní .NET Framework 3.5** je vybrané a pak vyberte **formulářová aplikace Windows** šablony.  
  
4.  Změnit projekt **název** k `ClientAppServicesDemo`a potom klikněte na tlačítko **OK**.  
  
     Nový projekt Windows Forms je otevřen v sadě Visual Studio.  
  
5.  Na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Zobrazí se Návrhář projektu.  
  
6.  Na **služby** kartu, vyberte možnost **povolit klientské aplikační služby**.  
  
7.  Ujistěte se, že **použít ověřování pomocí formulářů** nebude vybrána a potom nastavte **umístění služby ověřování**, **umístění služby role**, a **nastavení webu umístění služby** k `http://localhost:55555/AppServices`.  
  
8.  V jazyce Visual Basic na **aplikace** kartu, nastavte **režim ověřování** k **definovaného aplikací**.  
  
 Návrhář ukládá zadané nastavení v souboru app.config aplikace.  
  
 V tomto okamžiku aplikace je nakonfigurovaná pro přístup k všechny tři služby od stejného hostitele. V další části bude vytvoření hostitele jako jednoduchou aplikaci webové služby, umožňuje testování konfigurace klienta.  
  
## <a name="creating-the-application-services-host"></a>Vytváří se hostitel aplikačních služeb  
 V této části vytvoříte jednoduchou webovou aplikaci služby, která přistupuje k datům uživatelů ze souboru místní databáze SQL Server Compact. Potom, naplníte databázi pomocí [nástroje pro správu webu technologie ASP.NET](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Tato jednoduchá konfigurace můžete rychle otestovat klientskou aplikaci. Jako alternativu můžete nakonfigurovat hostitele webové služby pro přístup k datům uživatelů z celé databáze SQL serveru nebo prostřednictvím vlastní <xref:System.Web.Security.MembershipProvider> a <xref:System.Web.Security.RoleProvider> třídy. Další informace najdete v tématu [vytváření a konfiguraci této databáze systému SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 V následujícím postupu vytvoříte a nakonfigurujete AppServices webové služby.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Vytvoření a konfigurace hostitele služby aplikace  
  
1.  V **Průzkumníka řešení**, vyberte ClientAppServicesDemo řešení a pak na **souboru** nabídce vyberte možnost **přidat &#124; nový projekt**.  
  
2.  V **přidat nový projekt** v dialogu **typy projektů** podokně rozbalte **jazyka Visual Basic** nebo **Visual C#** uzel a vyberte  **Web** typ projektu.  
  
3.  Ujistěte se, že **rozhraní .NET Framework 3.5** je vybrané a pak vyberte **aplikaci webové služby ASP.NET** šablony.  
  
4.  Změnit projekt **název** k `AppServices` a potom klikněte na tlačítko **OK**.  
  
     Přidání nového projektu ASP.NET webové aplikace služby k řešení a Service1.asmx.vb nebo Service1.asmx.cs souboru se zobrazí v editoru.  
  
    > [!NOTE]
    >  V tomto příkladu se nepoužívá soubor Service1.asmx.vb nebo Service1.asmx.cs. Pokud chcete zachovat nezahlcený pracovní prostředí, můžete jej zavřete a odstraňte ho z **Průzkumníka řešení**.  
  
5.  V **Průzkumníka řešení**, vyberte projekt, aplikační služby a pak na **projektu** nabídce vyberte možnost **AppServices vlastnosti**.  
  
     Zobrazí se Návrhář projektu.  
  
6.  Na **webové** kartu, ujistěte se, že **použít Vývojový Server sady Visual Studio** zaškrtnuto.  
  
7.  Vyberte **specifického portu**, zadejte hodnotu `55555`a potom nastavte **virtuální cestu** k `/AppServices`.  
  
8.  Uložte všechny soubory.  
  
9. V **Průzkumníka řešení**, otevřete soubor Web.config a najít `<system.web>` počáteční značku.  
  
10. Přidejte následující kód před `<system.web>` značky.  
  
     `authenticationService`, `profileService`, A `roleService` prvky v tomto kódu povolte a nakonfigurujte aplikační služby. Pro testovací účely, `requireSSL` atribut `authenticationService` prvek je nastaven na hodnotu "false". `readAccessProperties` a `writeAccessProperties` atributy `profileService` element označuje, že `WebSettingsTestText` vlastnost je pro čtení a zápisu.  
  
    > [!NOTE]
    >  V produkčním kódu by měla vždy přístup k ověřovací službě, přes secure sockets layer (SSL, pomocí protokolu HTTPS). Informace o tom, jak nastavení protokolu SSL najdete v tématu [konfigurace Secure Sockets Layer (provozní příručce služby IIS 6.0)](https://go.microsoft.com/fwlink/?LinkId=91844).  
  
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
  
11. Přidejte následující kód za `<system.web>` tak, aby se v počáteční značce `<system.web>` elementu.  
  
     `profile` Element konfiguruje jedné webové nastavení s názvem `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 V následujícím postupu používají nástroje pro správu webu technologie ASP.NET k dokončení konfigurace služby a naplnit lokálního databázového souboru. Přidejte dva uživatele s názvem `employee` a `manager` patřící do dvě role se stejnými názvy. Hesla uživatelů se `employee!` a `manager!` v uvedeném pořadí.  
  
#### <a name="to-configure-membership-and-roles"></a>Ke konfiguraci členství a rolí  
  
1.  V **Průzkumníka řešení**, vyberte projekt, aplikační služby a pak na **projektu** nabídce vyberte možnost **konfigurace ASP.NET**.  
  
     **Nástroje pro správu webu technologie ASP.NET** se zobrazí.  
  
2.  Na **zabezpečení** klikněte na tlačítko **pomocí Průvodce nastavením zabezpečení můžete nakonfigurovat zabezpečení krok za krokem**.  
  
     **Průvodce nastavením zabezpečení** se zobrazí **úvodní** kroku.  
  
3.  Klikněte na tlačítko **Další**.  
  
     **Vyberte metodu přístupu** zobrazí krok.  
  
4.  Vyberte **z Internetu**. Tím se nakonfiguruje službu, aby používala ověřování pomocí formulářů místo ověřování Windows.  
  
5.  Klikněte na tlačítko **Další** dvakrát.  
  
     **Definovat role** zobrazí krok.  
  
6.  Vyberte **povolit role pro tento web**.  
  
7.  Klikněte na tlačítko **Další**. **Vytvořit novou roli** se zobrazil formulář.  
  
8.  V **nový název Role** textového pole, typ `manager` a potom klikněte na tlačítko **přidat roli**.  
  
     **Existující role** se zobrazí tabulka se zadanou hodnotou.  
  
9. V **nový název Role** textového pole nahraďte `manager` s `employee` a potom klikněte na tlačítko **přidat roli**.  
  
     Nová hodnota se zobrazí v **existující role** tabulky.  
  
10. Klikněte na tlačítko **Další**.  
  
     **Přidat nové uživatele** zobrazí krok.  
  
11. V **vytvořit uživatele** formulářů, zadejte následující hodnoty.  
  
  	|||  
  	|-|-|  
  	|**Uživatelské jméno**|`manager`|  
  	|**Heslo**|`manager!`|  
  	|**Potvrzení hesla**|`manager!`|  
  	|**E-mail**|`manager@contoso.com`|  
  	|**Bezpečnostní otázku**|`manager`|  
  	|**Zabezpečovací odpověď**|`manager`|  
  
12. Klikněte na tlačítko **vytvořit uživatele**.  
  
     Zobrazí se zpráva o úspěchu.  
  
    > [!NOTE]
    >  **E-mailu**, **bezpečnostní otázku**, a **zabezpečovací odpověď** hodnoty jsou vyžadované formuláře, ale nepoužívají se v tomto příkladu.  
  
13. Klikněte na tlačítko **pokračovat**.  
  
     **Vytvořit uživatele** formuláře zobrazí znovu.  
  
14. V **vytvořit uživatele** formulářů, zadejte následující hodnoty.  
  
  	|||  
  	|-|-|  
  	|**Uživatelské jméno**|`employee`|  
  	|**Heslo**|`employee!`|  
  	|**Potvrzení hesla**|`employee!`|  
  	|**E-mail**|`employee@contoso.com`|  
  	|**Bezpečnostní otázku**|`Employee`|  
  	|**Zabezpečovací odpověď**|`employee`|  
  
15. Klikněte na tlačítko **vytvořit uživatele**.  
  
     Zobrazí se zpráva o úspěchu.  
  
16. Klikněte na tlačítko **Dokončit**.  
  
     **Nástroje pro správu webu** se znovu zobrazí.  
  
17. Klikněte na tlačítko **uživatelé správce**.  
  
     Zobrazí se seznam uživatelů.  
  
18. Klikněte na tlačítko **upravit role** pro **zaměstnance** uživatele a pak vyberte **zaměstnance** role.  
  
19. Klikněte na tlačítko **upravit role** pro **správce** uživatele a pak vyberte **správce** role.  
  
20. Zavřete okno prohlížeče, který je hostitelem **nástroje pro správu webu**.  
  
21. Pokud se zobrazí okno se zprávou, s výzvou, pokud chcete znovu načíst upravené souboru Web.config, klikněte na tlačítko **Ano**.  
  
 Tím dokončíte nastavení webové služby. V tomto okamžiku můžete stisknutím klávesy F5 spusťte aplikaci klienta a **serveru ASP.NET Development Server** začne automaticky spolu s klientské aplikace. Server bude nadále spuštěna po ukončení aplikace, ale restartuje po restartování aplikace. Umožní vám to zjistit všechny změny provedené do souboru Web.config.  
  
 Pokud chcete zastavit server ručně, klikněte pravým tlačítkem na serveru ASP.NET Development Server ikonu v oznamovací oblasti na hlavním panelu a potom klikněte na **Zastavit**. To je užitečné a ujistěte se, že dojde k vyčištění restartování.  
  
## <a name="adding-forms-authentication"></a>Přidání ověřování pomocí formulářů  
 V následujícím postupu přidáte kód do hlavního formuláře, který se pokusí ověřit uživatele a odepře přístup, když uživatel zadá přihlašovací údaje neplatné. Použití pevně zakódované uživatelské jméno a heslo k otestování služby.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>K ověření uživatele v kódu aplikace  
  
1.  V **Průzkumníka řešení**, ClientAppServicesDemo projektu přidejte odkaz na sestavení System.Web.  
  
2.  Vyberte soubor Form1 a pak vyberte **zobrazení &#124; kód** z hlavní nabídky sady Visual Studio.  
  
3.  V editoru kódu přidejte následující příkazy do horní části souboru Form1.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  V **Průzkumníka řešení**, dvakrát klikněte na panel Form1 k zobrazení návrháře.  
  
5.  V Návrháři dvakrát klikněte na plochu formuláře ke generování <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události s názvem `Form1_Load`.  
  
     Zobrazí se editor kódu s kurzorem `Form1_Load` metody.  
  
6.  Přidejte následující kód, který `Form1_Load` metody.  
  
     Tento kód odepře přístup pro neověřené uživatele ukončením aplikace. Alternativně může povolit neověřené uživatele přístup do formuláře, ale odepřít přístup k určité funkce. Za normálních okolností je není pevně zakódovat uživatelské jméno a heslo tímto způsobem, ale je vhodný pro účely testování. V další části bude tento kód nahraďte robustnější kód, který se zobrazí dialogové okno přihlášení a obsahuje zpracování výjimek.  
  
     Všimněte si, že `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda je [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Tato metoda deleguje se do poskytovatele nakonfigurované ověřování svou práci a vrátí `true` Pokud je ověřování úspěšné. Vaše aplikace nevyžaduje, aby přímý odkaz na zprostředkovatele ověřování klienta.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Nyní můžete stisknutím klávesy F5 spusťte aplikaci a protože je zadat správné uživatelské jméno a heslo, zobrazí se formulář.  
  
> [!NOTE]
>  Pokud se nemůžete ke spuštění aplikace, zkuste zastavení serveru ASP.NET Development Server. Po restartování serveru, ověřte, zda je port nastaven na 55555.  
  
 Chcete-li místo toho zobrazí chybová zpráva, změňte <xref:System.Web.Security.Membership.ValidateUser%2A> parametry. Například nahradit druhý `"manager!"` parametr nesprávné heslo, jako jsou `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Přidání přihlašovacího formuláře jako poskytovatele přihlašovacích údajů  
 Můžete získat přihlašovací údaje uživatele v kódu aplikace a předat je do <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Často je však vhodné ponechat kódu získávání přihlašovacích údajů v případě, že chcete změnit později odděleně od kódu aplikace.  
  
 V následujícím postupu, je konfigurace aplikace pro používání poskytovatele přihlašovacích údajů a potom změňte vaše <xref:System.Web.Security.Membership.ValidateUser%2A> volání metody k předání <xref:System.String.Empty> pro oba parametry. Prázdné řetězce signalizuje, že <xref:System.Web.Security.Membership.ValidateUser%2A> metoda se má volat <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metoda poskytovatele nakonfigurované přihlašovací údaje.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Konfigurace aplikace pro používání poskytovatele přihlašovacích údajů  
  
1.  V **Průzkumníka řešení**, vyberte projekt ClientAppServicesDemo a pak na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Zobrazí se Návrhář projektu.  
  
2.  Na **služby** kartu, nastavte **volitelné: poskytovatele přihlašovacích údajů** následující hodnotu. Tato hodnota určuje název typu kvalifikovaného pro sestavení.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  V souboru kódu Form1 nahraďte kód v `Form1_Load` metodu s následujícím kódem.  
  
     Tento kód zobrazí uvítací zprávu a zavolá `ValidateUsingCredentialsProvider` metodu, která se v dalším kroku přidáte. Pokud uživatel není ověřen, `ValidateUsingCredentialsProvider` vrátí metoda `false` a `Form1_Load` metoda vrátí hodnotu. To žádný další kód zabraňuje spuštění před aplikací ukončí. Zobrazení uvítací zprávy je užitečné, aby bylo jasné, když se aplikace restartuje. Přidejte kód k restartování aplikace při implementaci odhlášení později v tomto názorném postupu.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Přidejte následující metodu po `Form1_Load` metody.  
  
     Tato metoda předává na prázdné řetězce `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metodu, která způsobí, že dialogové okno přihlášení se zobrazí. Pokud není k dispozici, službu ověřování <xref:System.Web.Security.Membership.ValidateUser%2A> vyvolá metoda výjimku <xref:System.Net.WebException>. V takovém případě `ValidateUsingCredentialsProvider` metoda zobrazí zprávu s upozorněním a požádá, pokud chce uživatel v režimu offline, zkuste to znovu. Tato funkce vyžaduje **uložit hodnoty hash hesla místně umožňující přihlášení offline** funkce popsané v [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Tato funkce je povolena ve výchozím nastavení pro nové projekty.  
  
     Pokud uživatel není ověřen, `ValidateUsingCredentialsProvider` metoda zobrazí chybovou zprávu a ukončí aplikaci. A konečně tato metoda vrací výsledek pokusu o ověření.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Vytváří se přihlašovací formulář  
 Poskytovatel přihlašovacích údajů je třída, která implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. Toto rozhraní obsahuje jedinou metodu s názvem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> , která vrací <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> objektu. Následující postupy popisují, jak vytvořit dialogové okno přihlášení, které implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> zobrazení samotného a vrátíte se přihlašovací údaje zadané uživatelem.  
  
 Samostatné procedury jsou uvedeny pro Visual Basic a C#, protože poskytuje jazyka Visual Basic **přihlašovací formulář** šablony. Toto uloží nějaký čas a úsilí kódování.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Chcete-li vytvořit dialogové okno přihlášení jako poskytovatel pověření v jazyce Visual Basic  
  
1.  V **Průzkumníka řešení**, vyberte projekt ClientAppServicesDemo a pak na **projektu** nabídce vyberte možnost **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **přihlašovací formulář** šablony, změně položky **název** k `Login.vb`a potom klikněte na tlačítko **přidat** .  
  
     Zobrazí se dialogové okno přihlášení v Návrháři formulářů Windows.  
  
3.  V návrháři, vyberte **OK** tlačítko a pak na **vlastnosti** okno, nastavte `DialogResult` k `OK`.  
  
4.  V návrháři, přidejte `CheckBox` ovládacího prvku na formulář v části **heslo** textového pole.  
  
5.  V **vlastnosti** okno, zadejte **(název)** hodnotu `rememberMeCheckBox` a **Text** hodnotu `&Remember me`.  
  
6.  Vyberte **zobrazení &#124; kód** z hlavní nabídky sady Visual Studio.  
  
7.  V editoru kódu přidejte následující kód do horní části souboru.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Upravte podpis třídy tak, aby třída implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Ujistěte se, že je kurzor po `IClientformsAuthenticationCredentialsProvider`, a potom stiskněte klávesu ENTER k vygenerování `GetCredentials` metody.  
  
10. Vyhledejte <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementace a nahraďte ho následujícím kódem.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Následující postup C# obsahuje celý kód pro dialogové okno jednoduchého přihlášení. Rozložení pro toto dialogové okno je trochu hrubý, ale je důležitou součástí <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementace.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Chcete-li vytvořit dialogové okno přihlášení jako poskytovatel pověření v jazyce C#  
  
1.  V **Průzkumníka řešení**, vyberte projekt ClientAppServicesDemo a pak na **projektu** nabídce vyberte možnost **přidat třídu**.  
  
2.  V **přidat novou položku** dialogovém okně Změnit **název** k `Login.cs`a potom klikněte na tlačítko **přidat**.  
  
     Login.cs soubor se otevře v editoru kódu.  
  
3.  Nahraďte kód následujícím kódem.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Teď můžete aplikaci spustit a zobrazit dialogové okno přihlášení se zobrazí. K otestování tohoto kódu, zkuste jiné přihlašovací údaje platné a platný a potvrďte, že dostanete formuláři pouze pomocí platných přihlašovacích údajů. Jsou platná uživatelská jména `employee` a `manager` s hesly `employee!` a `manager!` v uvedeném pořadí.  
  
> [!NOTE]
>  Nesmí být zvolen **zapamatovat** na tento bod nebo nebudou moct přihlásit jako jiný uživatel, dokud neimplementujete odhlášení později v tomto názorném postupu.  
  
## <a name="adding-role-based-functionality"></a>Přidání funkce na základě rolí  
 V následujícím postupu přidání tlačítka do formuláře a zobrazit pouze pro uživatele v roli správce.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Chcete-li změnit uživatelského rozhraní na základě role uživatele  
  
1.  V **Průzkumníka řešení**, v projektu ClientAppServicesDemo výběr možnosti Form1 a pak vyberte **zobrazení &#124; návrháře** z hlavní nabídky sady Visual Studio.  
  
2.  V návrháři, přidejte <xref:System.Windows.Forms.Button> ovládací prvek formuláře z **nástrojů**.  
  
3.  V **vlastnosti** okno, nastavte u tlačítka následující vlastnosti.  
  
  	|Vlastnost|Hodnota|  
  	|--------------|-----------|  
  	|**(Název)**|managerOnlyButton|  
  	|**Text**|& úkol Správce úloh|  
  	|**Viditelné**|`False`|  
  
4.  V editoru kódu pro Form1, přidejte následující kód do konce `Form1_Load` metody.  
  
     Tento kód volá `DisplayButtonForManagerRole` metodu, která se v dalším kroku přidáte.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Přidejte následující metodu za účelem třídy Form1.  
  
     Tato metoda volá <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metodu <xref:System.Security.Principal.IPrincipal> vrácených `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost. U aplikací nakonfigurován pro použití klientských aplikačních služeb, vrátí tato vlastnost <xref:System.Web.ClientServices.ClientRolePrincipal>. Protože tato třída implementuje <xref:System.Security.Principal.IPrincipal> rozhraní, není potřeba explicitně odkazovat.  
  
     Pokud je uživatel v roli "správce" `DisplayButtonForManagerRole` metody nastaví <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `managerOnlyButton` k `true`. Tato metoda také zobrazí chybovou zprávu, pokud <xref:System.Net.WebException> je vyvolána výjimka, což znamená, že služba role není k dispozici.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Metoda vždy vrátí `false` Pokud vypršela platnost přihlášení uživatele. Tím nedojde, pokud vaše aplikace volá <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metoda jednou krátce po ověření, jak je znázorněno v příkladu kódu v tomto návodu. Pokud vaše aplikace musí získat rolí uživatelů v jinou dobu, můžete přidat kód pro odhlášením uživatele, jehož přihlášení vypršela platnost. Pokud se všichni platní uživatelé jsou přiřazená rolím, můžete určit, jestli přihlášení vypršela platnost voláním <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> metody. Pokud se nezobrazí žádné role, přihlášení vypršela platnost. Příklad této funkce najdete v článku <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> metody. Tato funkce je nezbytné, pokud jste vybrali **vyžadují, aby uživatelé přihlásit znovu pokaždé, když vyprší platnost souboru cookie server** v konfiguraci vaší aplikace. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Pokud je ověření úspěšné, nastaví zprostředkovatele ověřování klienta <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost instance <xref:System.Web.ClientServices.ClientRolePrincipal> třídy. Tato třída implementuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metodu tak, aby práce se deleguje na nakonfigurované role zprostředkovatele. Jako dříve, kód vaší aplikace nevyžaduje, aby přímý odkaz na poskytovatele služeb.  
  
 Teď můžete spustit aplikaci a přihlaste se jako zaměstnanec zobrazíte, že na tlačítko Ne zobrazovat a pak se přihlaste jako správce, aby se tlačítko zobrazilo.  
  
## <a name="accessing-web-settings"></a>Přístup k webové nastavení  
 V následujícím postupu přidání textového pole do formuláře a vázat na webovém nastavení. Jako předchozí kód, který používá ověřování a rolí nastavení kód nepřistupuje k poskytovateli nastavení přímo. Místo toho používá silných `Settings` třídy (přistupuje jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v jazyce Visual Basic) sady Visual Studio vygenerovaný pro váš projekt.  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Použití nastavení webové uživatelské rozhraní  
  
1.  Ujistěte se, že **vývojový Server ASP.NET Web** pořád běží tak, že zkontrolujete oznamovací oblasti na hlavním panelu. Zastavení serveru restartujte aplikace (které spustí automaticky server), pak zavřete dialogové okno přihlášení.  
  
2.  V **Průzkumníka řešení**, vyberte projekt ClientAppServicesDemo a pak na **projektu** nabídce vyberte možnost **ClientAppServicesDemo vlastnosti**.  
  
     Zobrazí se Návrhář projektu.  
  
3.  Na **nastavení** klikněte na tlačítko **nastavení webu zatížení**.  
  
     A **přihlášení** zobrazí se dialogové okno.  
  
4.  Zadejte přihlašovací údaje pro zaměstnance nebo správce a klikněte na tlačítko **přihlásit**. Webové nastavení použijete je nakonfiguroval pro přístup ověřeným uživatelům, tedy kliknutím na **Přeskočit přihlášení** všechna nastavení se nenačte.  
  
     `WebSettingsTestText` Nastavení se zobrazí v Návrháři s výchozí hodnotou `DefaultText`. Kromě toho `Settings` třídu, která obsahuje `WebSettingsTestText` vlastnosti je vygenerována pro váš projekt.  
  
5.  V **Průzkumníka řešení**, v projektu ClientAppServicesDemo výběr možnosti Form1 a pak vyberte **zobrazení &#124; návrháře** z hlavní nabídky sady Visual Studio.  
  
6.  V návrháři, přidejte <xref:System.Windows.Forms.TextBox> ovládacího prvku na formuláři.  
  
7.  V **vlastnosti** okno, zadejte **(název)** hodnotu `webSettingsTestTextBox`.  
  
8.  V editoru kódu přidejte následující kód do konce `Form1_Load` metody.  
  
     Tento kód volá `BindWebSettingsTestTextBox` metodu, která se v dalším kroku přidáte.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Přidejte následující metodu za účelem třídy Form1.  
  
     Tato metoda vytvoří vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost `webSettingsTestTextBox` k `WebSettingsTestText` vlastnost `Settings` třídy vygenerované v předchozím kroku tohoto postupu. Tato metoda také zobrazí chybovou zprávu, pokud <xref:System.Net.WebException> je vyvolána výjimka, což znamená, že webová služba nastavení není k dispozici.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Obvykle použijete datové vazby k povolení automatického obousměrnou komunikaci mezi ovládacím prvkem a webové nastavení. Můžete však také přístup nastavení webu přímo jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. V Návrháři vyberte formulář a potom na **vlastnosti** okna, klikněte na tlačítko **události** tlačítko.  
  
11. Vyberte <xref:System.Windows.Forms.Form.FormClosing> události a poté stiskněte klávesu ENTER k vygenerování obslužné rutiny události.  
  
12. Vytvořena metoda nahraďte následujícím kódem.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Volání obsluhy události `SaveSettings` metodu, která se používá také podle funkce odhlášení, který bude v další části přidáte. `SaveSettings` Metoda nejdřív potvrdí, že uživatel není odhlášeni. Dělá to tak, že zkontrolujete <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> vlastnost <xref:System.Security.Principal.IIdentity> vrátí aktuální objekt zabezpečení. Aktuální objekt zabezpečení je získat pomocí `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> vlastnost. Pokud uživatel byl ověřen pro klientské aplikační služby, typ ověřování, který bude "ClientForms". `SaveSettings` Metody nelze jednoduše zaškrtněte <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> vlastnost vzhledem k tomu, že uživatel má po odhlášení platná identita Windows.  
  
     Pokud není uživatel přihlášen, `SaveSettings` volání metod <xref:System.Configuration.ApplicationSettingsBase.Save%2A> metodu `Settings` třídy vygenerované v předchozím kroku tohoto postupu. Tato metoda může vyvolat <xref:System.Net.WebException> Pokud vypršela platnost ověřovacího souboru cookie. K tomu dojde pouze v případě, že jste vybrali **vyžadují, aby uživatelé přihlásit znovu pokaždé, když vyprší platnost souboru cookie server** v konfiguraci vaší aplikace. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Obsluhovala platnost souborů cookie voláním <xref:System.Web.Security.Membership.ValidateUser%2A> zobrazíte dialogové okno přihlášení. Pokud uživatel úspěšně přihlásí, `SaveSettings` metoda se pokusí znovu uložit nastavení voláním sebe sama.  
  
     Jako v předchozím kódu `SaveSettings` metoda zobrazí chybovou zprávu, pokud není k dispozici vzdálené služby. Nastavení zprostředkovatele nelze získat přístup k vzdálené služby, jsou stále nastavení uloží do místní mezipaměti a znovu načten, když se aplikace restartuje.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Přidejte následující metodu za účelem třídy Form1.  
  
     Tento kód zpracovává <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> událostí a zobrazí upozornění, pokud některé z nastavení se neuložila. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Události nedojde, pokud nastavení služby není k dispozici, nebo pokud vypršela platnost ověřovacího souboru cookie. Jedním z příkladů nad tím, kdy <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> dojde k události je, pokud má uživatel již odhlášeni. Otestováním této obslužné rutiny události přidáním kódu odhlášení `SaveSettings` metody přímo před <xref:System.Configuration.ApplicationSettingsBase.Save%2A> volání metody. Odhlášení kód, který vám pomůže je popsané v další části.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Pro jazyk C#, přidejte následující kód do konce `Form1_Load` metody. Tento kód přidruží metody, které jste přidali v posledním kroku s <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> událostí.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Testování aplikace v tomto okamžiku, spustit jej několikrát jako zaměstnance a správce a zadejte jiné hodnoty do textového pole. Hodnoty se zachová napříč relacemi v jednotlivých uživatelů.  
  
## <a name="implementing-logout"></a>Implementace odhlašování  
 Když uživatel vybere **zapamatovat** zaškrtávací políčko při přihlašování, tato aplikace se automaticky ověření uživatele při dalším spuštění. Automatické ověřování bude pokračovat, pak když je aplikace v režimu offline, nebo do vypršení platnosti souboru cookie pro ověřování. V některých případech však více uživatelé budou potřebovat přístup k aplikaci nebo jenom jednoho konkrétního uživatele může čas od času přihlášení pomocí různých přihlašovacích údajů. Pokud chcete povolit tento scénář, musí implementovat funkce odhlášení, jak je popsáno v následujícím postupu.  
  
#### <a name="to-implement-logout-functionality"></a>K implementaci funkcionality odhlášení  
  
1.  V Návrháři Form1 přidat <xref:System.Windows.Forms.Button> ovládací prvek formuláře z **nástrojů**.  
  
2.  V **vlastnosti** okno, zadejte **(název)** hodnotu `logoutButton` a **Text** hodnotu **& Odhlásit**.  
  
3.  Dvakrát klikněte `logoutButton` ke generování <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     Zobrazí se editor kódu s kurzorem `logoutButton_Click` metody.  
  
4.  Nahraďte generované `logoutButton_Click` metodu s následujícím kódem.  
  
     Tato obslužná rutina události zavolá nejprve `SaveSettings` metodu, která jste přidali v předchozí části. Obslužná rutina události zavolá <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> metody. Pokud není k dispozici, službu ověřování <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> vyvolá metoda výjimku <xref:System.Net.WebException>. V takovém případě `logoutButton_Click` metoda zobrazí zprávu upozornění a přepne dočasně do režimu offline na odhlášení uživatele. Offline režim je popsané v další části.  
  
     Odhlášení odstraní soubor cookie ověřování pomocí místních, tak, že se přihlášení se bude vyžadovat, když se aplikace restartuje. Obslužná rutina události po odhlašování, restartování aplikace. Když se aplikace restartuje, zobrazí zobrazení uvítací zprávy dialogové okno přihlášení. Zobrazení uvítací zprávy vyjasňuje, která se aplikace restartuje. To zabraňuje nejasnostem, pokud uživatel musí přihlásit k uložení nastavení a pak musíte se přihlásit znovu vzhledem k tomu, že se aplikace restartuje.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 K otestování funkce odhlášení, spusťte aplikaci a vyberte **zapamatovat** v dialogovém okně přihlášení. Potom zavřete a znovu spusťte aplikaci, aby potvrďte, že už máte k přihlášení. Nakonec restartování aplikace kliknutím při odhlášení.  
  
## <a name="enabling-offline-mode"></a>Povolení Offline režimu  
 V následujícím postupu přidáte zaškrtávací políčko na formulář umožňuje uživateli zadat offline režimu. Vaše aplikace určuje offline režimu tak, že nastavíte `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> vlastnost `true`. Offline stav je uložený na místní pevný disk v umístění indikován <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> vlastnost. To znamená, že na jednotlivé uživatele, každou aplikaci je uložena v režimu offline.  
  
 Všechny klientské žádosti o aplikace služby v offline režimu, načtou data z místní mezipaměti namísto pokusu o přístup ke službám. Ve výchozí konfiguraci místní data zahrnují zašifrované heslo uživatele. To umožňuje uživateli přihlásit, když je aplikace v režimu offline. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Pokud chcete povolit offline režim v aplikaci  
  
1.  V **Průzkumníka řešení**, v projektu ClientAppServicesDemo výběr možnosti Form1 a pak vyberte **zobrazení &#124; návrháře** z hlavní nabídky sady Visual Studio.  
  
2.  V návrháři, přidejte <xref:System.Windows.Forms.CheckBox> ovládacího prvku na formuláři.  
  
3.  V **vlastnosti** okno, zadejte **(název)** hodnotu `workOfflineCheckBox` a **Text** hodnotu **& pracovní offline**.  
  
4.  V **vlastnosti** okna, klikněte na tlačítko **události** tlačítko.  
  
5.  Vyberte <xref:System.Windows.Forms.CheckBox.CheckedChanged> události a poté stiskněte klávesu ENTER k vygenerování obslužné rutiny události.  
  
6.  Vytvořena metoda nahraďte následujícím kódem.  
  
     Tento kód aktualizuje <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> hodnotu a tiše revalidates uživatele, když se vrátí do režimu online. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> – Metoda používá přihlašovací údaje v mezipaměti, takže není nutné explicitně přihlášení uživatele. Pokud ověřovací služby není k dispozici, zobrazí se zpráva s upozorněním a aplikace zůstává v režimu offline.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Metoda je pouze ke zvýšení pohodlí. Protože nemá žádné návratovou hodnotu, se nesmí uvádět, zda opětovné ověření se nezdařilo. Opětovné ověření může selhat, například pokud jste změnili přihlašovací údaje uživatele na serveru. V takovém případě můžete chtít zahrnout kód, který explicitně ověřuje uživatele, pokud selže volání služby. Další informace najdete v části Nastavení webového přístupu k dříve v tomto návodu.  
  
     Po opětovné ověření, tento kód uloží změny do místní nastavení webu voláním `SaveSettings` metodu, která jste přidali dříve. Pak načte všechny nové hodnoty na serveru pomocí volání <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> metoda projektu `Settings` třídy (přistupuje jako `Properties.Settings.Default` v jazyce C# a `My.Settings` v jazyce Visual Basic).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Přidejte následující kód do konce `Form1_Load` metoda Ujistěte se, že, zaškrtnutí políčka zobrazuje aktuální stav připojení.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Dokončení tohoto postupu ukázková aplikace. Testování offline funkcí, spusťte aplikaci, přihlaste se jako zaměstnanec nebo správce a vyberte **práce offline**. Změnit hodnotu v textovém poli a pak ukončete aplikaci. Restartování aplikace. Předtím, než se přihlásíte, klikněte pravým tlačítkem na serveru ASP.NET Development Server ikonu v oznamovací oblasti na hlavním panelu a potom klikněte na **Zastavit**. Pak se přihlásit jako normální. I v případě, že server není spuštěn, se můžete stále přihlásit. Upravte hodnotu textového pole, ukončení a restartování zobrazíte upravené hodnoty.  
  
## <a name="summary"></a>Souhrn  
 V tomto návodu jste zjistili, jak povolit a použití klientských aplikačních služeb v aplikaci Windows Forms. Po nastavení testovací server, přidat kód do vaší aplikace k ověřování uživatelů a načíst role uživatele a nastavení aplikací ze serveru. Také jste zjistili, jak povolit offline režimu, aby vaše aplikace používá mezipaměť místních dat namísto vzdálené služby, pokud připojení není k dispozici.  
  
## <a name="next-steps"></a>Další kroky  
 V reálné aplikaci bude přístup k datům pro mnoho uživatelů ze vzdáleného serveru, který nemusí být vždy k dispozici, nebo může ujmout bez předchozího upozornění. K zajištění robustní aplikace, které musí správně reagovat na situace, kdy služba není k dispozici. Tento názorný postup obsahuje bloky try/catch k zachycování <xref:System.Net.WebException> a zobrazí chybovou zprávu, pokud služba není k dispozici. V produkčním kódu můžete chtít zpracovávat tento případ přepnutí do offline režimu, ukončením aplikace nebo zamítáte přístup ke konkrétním funkcím.  
  
 Pokud chcete zvýšit zabezpečení aplikace, ujistěte se, že vám pomůže s podrobným aplikace a serveru před nasazením.  
  
## <a name="see-also"></a>Viz také  
 [Klientské aplikační služby](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Nástroje pro správu webu technologie ASP.NET](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Vytváření a konfiguraci této databáze systému SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [Návod: Použití aplikačními službami ASP.NET](https://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
