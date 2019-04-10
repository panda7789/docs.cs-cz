---
title: Řešení potíží se zasíláním zpráv zařazovaných do front
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: c85b0701c870fe2b4a3c11dc384e890e1ed001dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322040"
---
# <a name="troubleshooting-queued-messaging"></a>Řešení potíží se zasíláním zpráv zařazovaných do front
Tato část obsahuje běžné dotazy a řešení potíží s pomoci při používání front ve Windows Communication Foundation (WCF).  
  
## <a name="common-questions"></a>Nejčastější dotazy  
 **DOTAZ:** Můžu použít WCF Beta 1 a mám nainstalovanou opravu hotfix služby MSMQ. Je potřeba odebrat opravu hotfix?  
  
 **ODPOVĚĎ:** Ano. Tato oprava hotfix se už nepodporuje. WCF teď funguje v MSMQ bez požadavek na opravu hotfix.  
  
 **DOTAZ:** Existují dvě vazby pro službu MSMQ: <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Kterou možnost mám použít a kdy?  
  
 **ODPOVĚĎ:** Použít <xref:System.ServiceModel.NetMsmqBinding> Pokud chcete použít pro komunikaci ve frontě mezi dvěma aplikacemi WCF služby MSMQ jako přenosového mechanismu. Použít <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> Pokud chcete použít existující aplikacím služby MSMQ ke komunikaci s novou aplikací služby WCF.  
  
 **DOTAZ:** Je nutné upgradovat služby MSMQ používat <xref:System.ServiceModel.NetMsmqBinding> a `MsmqIntegration` vazby?  
  
 **ODPOVĚĎ:** Ne. Obě vazby pracovat s MSMQ 3.0 na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Některé funkce vazby k dispozici, když upgradujete na službu MSMQ 4.0 v [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **DOTAZ:** Jaké funkce <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> vazeb jsou k dispozici v MSMQ 4.0, ale ne v MSMQ 3.0?  
  
 **ODPOVĚĎ:** K dispozici v MSMQ 4.0, ale ne v MSMQ 3.0 spadají následující funkce:  
  
-   Vlastní frontu nedoručených zpráv je podporován pouze v MSMQ 4.0.  
  
-   Služba MSMQ 3.0 a 4.0 zpracování jinak nezpracovatelných zpráv.  
  
-   Pouze služba MSMQ 4.0 podporuje vzdálené transakce čtení.  
  
 Další informace najdete v tématu [rozdíly ve funkcích služby Řízení front ve Windows Vista, Windows Server 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **DOTAZ:** Můžete použít služby MSMQ 3.0 na jedné straně komunikaci ve frontě a MSMQ 4.0 na druhé straně?  
  
 **ODPOVĚĎ:** Ano.  
  
 **DOTAZ:** Chci, aby stávající služby MSMQ aplikace integrovat nové WCF klientů nebo serverů. Je potřeba upgradovat na obou stranách Moje MSMQ infrastruktury?  
  
 **ODPOVĚĎ:** Ne. Není potřeba upgradovat na službu MSMQ 4.0 na obou stranách.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Tato část obsahuje odpovědi na nejčastější řešení problémů. Některé problémy, které jsou známé omezení jsou také popsány v poznámkách k verzi.  
  
 **DOTAZ:** Provést použít soukromé fronty a získat následující výjimku: `System.InvalidOperationException`: Adresa URL je neplatná. Adresa URL pro frontu nesmí obsahovat znak "$". Použijte syntaxi v adrese NET.MSMQ://machine/private/queueName k adresování soukromé fronty.  
  
 **ODPOVĚĎ:** Zkontrolujte, zda fronta identifikátor URI (Uniform Resource) ve vaší konfiguraci a kód. Nepoužívejte znak "$" v identifikátoru URI. Například adresování soukromé fronty s názvem OrdersQueue, zadejte jako net.msmq://localhost/private/ordersQueue identifikátoru URI.  
  
 **DOTAZ:** Volání `ServiceHost.Open()` na aplikaci ve frontě vyvolala následující výjimku: `System.ArgumentException`: Základní adresa nesmí obsahovat řetězec dotazu identifikátoru URI. Proč?  
  
 **ODPOVĚĎ:** Zkontrolujte fronty identifikátor URI v konfiguračním souboru a ve vašem kódu. Zatímco fronty MSMQ podporují použití "?" znak, identifikátory URI tento znak interpretovat jako začátek řetězce dotazu. Chcete-li tomuto problému vyhnout, použijte názvy front, které neobsahují "?" znaků.  
  
 **DOTAZ:** Moje odesílání úspěšné, ale žádné operaci služby se vyvolá u příjemce. Proč?  
  
 **ODPOVĚĎ:** Chcete-li zjistit odpověď, seznámení se základními následujícím kontrolním seznamu:  
  
-   Zkontrolujte, jestli jsou kompatibilní s záruky zadaný transakční fronty požadavků. Mějte na paměti následující zásady:  
  
    -   Můžete odeslat trvalý zprávy (datagramů a relace) s "právě jednou" záruky (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) pouze pro transakční frontu.  
  
    -   Můžete odeslat relace pouze s "právě jednou" záruky.  
  
    -   Transakce se vyžaduje pro příjem zpráv v transakční frontě relaci.  
  
    -   Můžete odesílat nebo přijímat přechodné nebo trvalé zprávy (pouze datagramy) s žádné záruky (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) pouze pro transakční frontu.  
  
-   Zkontrolujte fronty nedoručených zpráv. Pokud zjistíte, že zprávy, zjistit, proč se doručit.  
  
-   Zkontrolujte fronty odesílaných zpráv pro připojení nebo řeší problémy.  
  
 **DOTAZ:** Zadání vlastní frontu nedoručených zpráv, ale při spuštění aplikace odesílatele, získat výjimku, která nebyla nalezena fronty nedoručených zpráv nebo odesílací aplikace nemá oprávnění pro frontu nedoručených zpráv. Proč k tomu dochází?  
  
 **ODPOVĚĎ:** Vlastní frontu nedoručených zpráv identifikátor URI musí obsahovat "localhost" ani název počítače v první segment, například net.msmq://localhost/private/myAppdead-letter fronty.  
  
 **DOTAZ:** Platí to vždy nezbytné k definování vlastní frontu nedoručených zpráv, nebo je výchozí fronta nedoručených zpráv?  
  
 **ODPOVĚĎ:** Pokud jsou záruky "právě jednou" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a pokud nezadáte vlastní frontu nedoručených zpráv, výchozí hodnota je systémová transakční fronty nedoručených zpráv.  
  
 Pokud záruky k žádným nedošlo (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), pak výchozí hodnota je žádné funkce fronty nedoručených zpráv.  
  
 **DOTAZ:** Služba se vyvolá na SvcHost.Open s zpráva "EndpointListener požadavky nelze splnit třídou ListenerFactory". Proč?  
  
 A. Zkontrolujte váš kontraktu služby. Možná jste zapomněli vložit "IsOneWay =`true`" na všechny operace služby. Fronty podporují pouze jednosměrné servisní operace.  
  
 **DOTAZ:** Existují zprávy ve frontě, ale je vyvolána žádná operace služby. V čem je problém?  
  
 **ODPOVĚĎ:** Určete, pokud je váš hostitel služby selhal. Můžete zkontrolovat, že prohlížení trasování nebo implementaci `IErrorHandler`. Chyby služby hostitele, ve výchozím nastavení, pokud se zjistí počet nezpracovatelných zpráv.  
  
 **DOTAZ:** Existují zprávy ve frontě, ale můj Web hostovaný ve frontě služby získávání neaktivovat. Proč?  
  
 **ODPOVĚĎ:** Nejběžnějším důvodem je oprávnění.  
  
1. Ujistěte se, že `NetMsmqActivator` je proces spuštěn a její identitu `NetMsmqActivator` procesu je uveden pro čtení a hledání oprávnění ve frontě.  
  
2. Pokud `NetMsmqActivator` je monitorování front ve vzdáleném počítači, ujistěte se, že `NetMsmqActivator` neběží pod token s omezeným přístupem. Ke spuštění `NetMsmqActivator` neomezený tokenu:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Nesouvisí se zabezpečením související webového hostitele problémy najdete: [Webhosting Frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **DOTAZ:** Co je nejjednodušší způsob, jak relace přístupu?  
  
 **ODPOVĚĎ:** Nastavení automatického dokončování =`true` na operaci, která odpovídá na poslední zprávy v relaci a nastavit automatické dokončování =`false` na všechny zbývající operace služby.  
  
 **DOTAZ:** Kde najdete odpovědi na běžné dotazy na službu MSMQ?  
  
 **ODPOVĚĎ:** Další informace o MSMQ najdete v tématu [Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **DOTAZ:** Proč Moje služba vyvolá `ProtocolException` při čtení z fronty, která obsahuje obě relace zpráv zařazených do fronty a datagram zpráv zařazených do fronty?  
  
 **ODPOVĚĎ:** Je zásadní rozdíl v relaci způsobem ve frontě zpráv a zprávy ve frontě datagram se skládají. Z toho důvodu služba, která očekává ke čtení zprávy ve frontě relace nemůže přijímat zprávy ve frontě datagram a do služby očekávající ke čtení zprávy ve frontě datagram nemůže přijímat zprávy relace. Při čtení oba typy zpráv ze stejné fronty vyvolá následující výjimku:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Fronty nedoručených zpráv systému, stejně jako všechny vlastní frontu nedoručených zpráv, je zvlášť náchylné k tomuto problému, když aplikace pošle obě relace zpráv zařazených do fronty a zprávy pro datagram ze stejného počítače zařazené do fronty. Pokud zprávu nejde úspěšně odeslat, je přesunuta do fronty nedoručených zpráv. Za těchto okolností je možné mít relace a datagram zprávy ve frontě nedoručených zpráv. Neexistuje žádný způsob, jak oddělit oba typy zpráv za běhu při čtení z fronty, proto by neměly odesílat aplikace obě relace zpráv zařazených do fronty a zprávy pro datagram ze stejného počítače zařazené do fronty.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integrace MSMQ: Řešení konkrétních potíží  
 **DOTAZ:** Když mi odeslat zprávu nebo při otevření hostitele služby, obdržím chybu, která označuje, že schéma je nesprávný. Proč?  
  
 **ODPOVĚĎ:** Při použití integrace vazby služby MSMQ musí používat schéma msmq.formatname. Například msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Ale pokud chcete zadat vlastní frontu nedoručených zpráv, je nutné použít schéma net.msmq.  
  
 **DOTAZ:** Při použití veřejných nebo privátních formát názvu a otevřít hostitele služby v [!INCLUDE[wv](../../../../includes/wv-md.md)], se zobrazí chyba. Proč?  
  
 **ODPOVĚĎ:** Kanál integrace WCF na [!INCLUDE[wv](../../../../includes/wv-md.md)] kontroluje, pokud do dílčí fronty můžete otevřít pro hlavní aplikaci fronty pro zpracování nezpracovatelných zpráv. Název dílčí fronty je odvozen z msmq.formatname, které URI předaný k naslouchacímu procesu. Název dílčí fronty ve službě MSMQ lze pouze název v přímém formátu. Proto se zobrazí chyba. Změňte identifikátor URI fronty na název v přímém formátu.  
  
 **DOTAZ:** Při příjmu zprávy z aplikace služby MSMQ, zpráva umístěná ve frontě a není, přečtěte si přijímající aplikace WCF. Proč?  
  
 **ODPOVĚĎ:** Zkontrolujte, zda zpráva nemá tělo. Pokud zpráva nemá žádný text, ignoruje integrace služby MSMQ zprávy. Implementace `IErrorHandler` informováni o výjimkách a zkontrolovat trasování.  
  
### <a name="security-related-troubleshooting"></a>Řešení potíží souvisejících se zabezpečením  
 **DOTAZ:** Při spuštění ukázky, která používá výchozí vazbu v režimu pracovní skupiny, vypadá to, že odesílání zprávy, ale nepřijímají příjemce.  
  
 **ODPOVĚĎ:** Ve výchozím nastavení jsou zprávy podepsány pomocí služby MSMQ vnitřní certifikát, který vyžaduje adresářové služby Active Directory. V režimu pracovní skupiny protože služba Active Directory není k dispozici, podepisování zprávy selže. Proto jsou zprávy ve frontě nedoručených zpráv a je označen příčinu selhání, jako je například "Chybný podpis".  
  
 Alternativním řešením je vypnout zabezpečení. To se provádí nastavením <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> aby to fungovalo v režimu pracovní skupiny.  
  
 Jiným řešením je zobrazíte <xref:System.ServiceModel.MsmqTransportSecurity> z <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> vlastnost a nastavte ho na <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>a nastavit certifikát klienta.  
  
 Zatím jiné alternativním řešením je instalace služby MSMQ s integrací služby Active Directory.  
  
 **DOTAZ:** Při odeslání zprávy s využitím výchozí vazby (přenosu zabezpečení zapnutá) ve službě Active Directory do fronty, se zobrazí zpráva "vnitřní certifikát nebyl nalezen". Jak to mohu napravit?  
  
 **ODPOVĚĎ:** To znamená, že certifikát ve službě Active Directory pro odesílatele musí obnovit. Chcete-li to provést, otevřete **ovládací panely**, **nástroje pro správu**, **Správa počítače**, klikněte pravým tlačítkem na **MSMQ**a vyberte **Vlastnosti**. Vyberte **uživatelský certifikát** kartě a klikněte na tlačítko **obnovit** tlačítko.  
  
 **DOTAZ:** Když mi odeslat zprávu pomocí <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> a určete certifikát, který chcete použít, se zobrazí zpráva "Neplatné certifikátu". Jak to mohu napravit?  
  
 **ODPOVĚĎ:** Úložiště certifikátů místního počítače nelze použít s režimem certifikátu. Budete muset zkopírujte certifikát do úložiště pro aktuálního uživatele pomocí modulu snap-in certifikátu z úložiště certifikátů počítače. Pokud chcete získat certifikát modul snap-in:  
  
1. Klikněte na tlačítko **Start**vyberte **spustit**, typ `mmc`a klikněte na tlačítko **OK**.  
  
2. V **konzoly Microsoft Management Console**, otevřete **souboru** nabídky a vybereme **Přidat/odebrat modul Snap-in**.  
  
3. V **Přidat/odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **přidat** tlačítko.  
  
4. V **přidat samostatný modul Snap-in** dialogové okno, vyberte certifikáty a klikněte na tlačítko **přidat**.  
  
5. V **certifikáty** modul snap-in dialogu **Můj uživatelský účet,** a klikněte na tlačítko **Dokončit**.  
  
6. V dalším kroku přidejte druhý certifikáty modulu snap-in v předchozích krocích, ale tentokrát vyberte **účet počítače** a klikněte na tlačítko **Další**.  
  
7. Vyberte **místního počítače** a klikněte na tlačítko **Dokončit**. Teď můžete přetáhnout a vyřadit certifikáty z úložiště certifikátů počítače pro úložiště pro aktuálního uživatele.  
  
 **DOTAZ:** Když Služba čte z fronty na jiný počítač v režimu pracovní skupiny, se zobrazit výjimka "přístup byl odepřen".  
  
 **ODPOVĚĎ:** V režimu pracovní skupiny pro vzdálenou aplikaci získat přístup k frontě aplikace musí mít oprávnění pro přístup k frontě. Přidání "anonymní přihlášení" do fronty seznam řízení přístupu (ACL) a přiřaďte jí oprávnění ke čtení.  
  
 **DOTAZ:** Když klient služby sítě (nebo libovolného klienta, který nemá doménový účet) odesílá zprávy ve frontě, odesílání selže s neplatným certifikátem. Jak to mohu napravit?  
  
 **ODPOVĚĎ:** Zkontrolujte konfiguraci vazby. Výchozí vazba má MSMQ zabezpečení přenosu nastavená na aby bylo možné podepisování zpráv. Vypněte jej.  
  
### <a name="remote-transacted-receives"></a>Přijímá vzdálené nepodporuje transakce  
 **DOTAZ:** Když mám frontu počítače a služby WCF, která čte zprávy z fronty v počítači B (vzdálené transakční přijímat scénář), zprávy se číst z fronty. Trasovací informace označuje úspěšný příjem, zpráva "transakci nelze importovat." Co můžete dělat na tento problém vyřešit?  
  
 **ODPOVĚĎ:** Existují tři možné důvody:  
  
-   Pokud jste v režimu domény, vzdálené transakční přijímat vyžaduje přístup k síti Microsoft distribuované transakce koordinátor (MSDTC). Můžete povolit pomocí **přidat nebo odebrat součásti**.  
  
     ![Snímek obrazovky zobrazující povolení síťové služby DTC přístup.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)  
  
-   Zkontrolujte režim ověřování pro komunikaci se správcem transakcí. Pokud jste v režimu pracovní skupiny, je nutné vybrat "Ověření není vyžadováno". Pokud jste v režimu domény, musíte vybrat "Je vyžadováno vzájemné ověření".  
  
     ![Povolení transakce XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   Ujistěte se, že služba MSDTC je v seznamu výjimek v **brány Firewall pro připojení k Internetu** nastavení.  
  
-   Ujistěte se, že používáte [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje vzdálené transakce čtení. MSMQ na starších verzích Windows nepodporuje vzdálené transakce čtení.  
  
 **DOTAZ:** Při čtení z fronty služby je síťová služba, například ve webovém hostitele, proč se zobrazí odepření přístupu výjimka je vyvolána při čtení z fronty?  
  
 **ODPOVĚĎ:** Síťový přístup pro čtení služby musí být přidána do fronty seznamu ACL k zajištění, že síťová služba může číst zprávy z fronty.  
  
 **DOTAZ:** Můžete použít aktivační služba MSMQ k aktivaci aplikací založených na zprávy ve frontě na vzdáleném počítači?  
  
 **ODPOVĚĎ:** Ano. K tomu, musíte nakonfigurovat aktivace služby MSMQ pro spuštění jako síťové služby a přidat přístup k síťové službě do fronty ve vzdáleném počítači.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Vazby služby MSMQ vlastní pomocí ReceiveContext povoleno  
 Při použití vlastní vazby služby MSMQ s <xref:System.ServiceModel.Channels.ReceiveContext> povoleno zpracování příchozí zprávy budou použít vláknu fondu vláken, protože nativní služby MSMQ nepodporuje dokončení vstupně-výstupních operací pro asynchronní <xref:System.ServiceModel.Channels.ReceiveContext> obdrží. Důvodem je, že zpracování takové zprávy používá vnitřní transakce pro <xref:System.ServiceModel.Channels.ReceiveContext> a MSMQ nepodporuje asynchronní zpracování. Chcete-li vyřešit tento problém můžete přidat <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> ke koncovému bodu vynutit synchronní zpracování, nebo nastavte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> na hodnotu 1.
