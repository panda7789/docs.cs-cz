---
title: Řešení potíží se zasíláním zpráv zařazovaných do front
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1342f2383e7cf2aa15ea60be03c93044e4332612
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-queued-messaging"></a>Řešení potíží se zasíláním zpráv zařazovaných do front
Tato část obsahuje běžné otázky a řešení potíží pomoci při používání front v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="common-questions"></a>Nejčastější dotazy  
 **Otázka:** použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Beta 1 a I nainstalována oprava hotfix služby MSMQ. Je potřeba odebrat opravu hotfix?  
  
 **Odpověď:** Ano. Tato oprava hotfix již není podporována. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Teď funguje na MSMQ bez požadavek opravu hotfix.  
  
 **Otázka:** existují dvě vazeb pro služby MSMQ: <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Co je třeba použít a kdy?  
  
 **Odpověď:** použít <xref:System.ServiceModel.NetMsmqBinding> když chcete používat služby MSMQ jako přenosového mechanismu pro komunikaci ve frontě mezi dvěma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Použít <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> když chcete používat existující aplikacím služby MSMQ pro komunikaci se nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
 **Otázka:** muset upgradovat služby MSMQ používat <xref:System.ServiceModel.NetMsmqBinding> a `MsmqIntegration` vazby?  
  
 **Odpověď:** ne. Obě vazby pracovat s MSMQ 3.0 na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Při upgradu na MSMQ 4.0 v je k dispozici určitých funkcí vazby [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **Otázka:** jaké funkce <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> vazby jsou k dispozici v MSMQ 4.0, ale ne v MSMQ 3.0?  
  
 **Odpověď:** v MSMQ 4.0, ale ne v MSMQ 3.0 k dispozici jsou následující funkce:  
  
-   Vlastní frontu nedoručených zpráv je podporována pouze v MSMQ 4.0.  
  
-   Služba MSMQ 3.0 a 4.0 zpracovávat jinak poškozených zpráv.  
  
-   Pouze MSMQ 4.0 podporuje vzdálené zpracovaných pro čtení.  
  
 Další informace najdete v tématu [rozdíly služby Řízení front funkcí v systému Windows Vista, Windows Server 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **Otázka:** můžete použít MSMQ 3.0 na jedné straně komunikace ve frontě a MSMQ 4.0 na druhé straně?  
  
 **Odpověď:** Ano.  
  
 **Otázka:** chcete integrovat existující aplikacím služby MSMQ nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů nebo serverů. Je potřeba upgradovat obou stranách Moje MSMQ infrastruktury?  
  
 **Odpověď:** ne. Nemáte k upgradu služby MSMQ 4.0 na obou stranách.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Tato část obsahuje odpovědi na nejčastější řešení problémů. Některé problémy, které jsou známé omezení jsou také popsány v poznámkách k verzi.  
  
 **Otázka:** pokouším použít soukromé fronty se zobrazila následující výjimky: `System.InvalidOperationException`: adresa URL je neplatná. Adresa URL pro frontu nesmí obsahovat znak "$". Pomocí syntaxe v net.msmq://machine/private/queueName vyřešit soukromou frontu.  
  
 **Odpověď:** zkontrolujte ve frontě identifikátor URI (Uniform Resource) v konfiguraci a kódu. Nepoužívejte "$" znak v identifikátoru URI. Například adresa soukromou frontu s názvem OrdersQueue, zadejte jako net.msmq://localhost/private/ordersQueue identifikátor URI.  
  
 **Otázka:** volání `ServiceHost.Open()` na Moje aplikace ve frontě, vyvolá následující výjimky: `System.ArgumentException`: základní adresa nesmí obsahovat řetězec dotazu identifikátoru URI. Proč?  
  
 **Odpověď:** zkontrolujte fronty URI v konfiguračním souboru a v kódu. Při fronty služby MSMQ podporují použití '?' znak, identifikátory URI interpretovat tento znak jako začátek řetězce dotazu. Chcete-li tomuto problému vyhnout, použijte názvy front, které neobsahují '?' znaků.  
  
 **Otázka:** Moje odesílání úspěšné, ale žádná operace služby je volána, příjemce. Proč?  
  
 **Odpověď:** Pokud chcete zjistit, odpověď, postupujte následujícím kontrolním seznamu:  
  
-   Zkontrolujte, jestli jsou kompatibilní s záruky zadaný transakční fronty požadavků. Vezměte na vědomí následující zásady:  
  
    -   Můžete odeslat trvanlivý zprávy (datagramy a relací) s "přesně jedno" záruky (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) pouze pro transakční fronty.  
  
    -   Můžete odeslat relací pouze s "přesně jedno" záruky.  
  
    -   Transakce se vyžaduje pro příjem zprávy v relaci z transakcí fronty.  
  
    -   Můžete odeslat nebo přijmout volatile nebo trvanlivý zprávy (pouze datagramy) s žádné záruky (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) pouze pro transakční fronty.  
  
-   Zkontrolujte frontu nedoručených zpráv. Pokud zjistíte, že zprávy, zjistěte, proč nebyly doručit.  
  
-   Zkontrolujte odchozí fronty pro připojení nebo řešení problémů.  
  
 **Otázka:** zadali vlastní frontu nedoručených zpráv, ale při spuštění aplikace sender se zobrazí výjimka, která nebyla nalezena fronty nedoručených zpráv nebo odesílající aplikací nemá oprávnění pro frontu nedoručených zpráv. Proč je této situaci?  
  
 **Odpověď:** vlastní identifikátor URI fronty nedoručených zpráv musí obsahovat "localhost" nebo název počítače v první segment, například net.msmq://localhost/private/myAppdead-letter fronty.  
  
 **Otázka:** je vždy nutné definovat vlastní frontu nedoručených zpráv, nebo je k dispozici výchozí fronty nedoručených zpráv?  
  
 **Odpověď:** Pokud záruky, pokud jsou "přesně jedno" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a pokud nezadáte vlastní frontu nedoručených zpráv, výchozí hodnota je platná pro celý systém transakční fronty nedoručených zpráv.  
  
 Pokud záruky, pokud jsou none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), pak výchozí hodnota je žádné funkce frontu nedoručených zpráv.  
  
 **Otázka:** Moje služba vyvolává na SvcHost.Open zprávou "požadavky na EndpointListener nelze splnit ListenerFactory". Proč?  
  
 A. Zkontrolujte vaše kontrakt služby. Jste zapomněli uvést "IsOneWay =`true`" na všechny operace služby. Fronty podporují pouze jednosměrné služby operace.  
  
 **Otázka:** existují zprávy ve frontě, ale právě se vyvolává žádná operace služby. Co je problém?  
  
 **Odpověď:** určit, pokud je váš hostitel služby s chybou. Můžete zkontrolovat prohlížení trasování nebo implementace `IErrorHandler`. Služba chyb hostitele, ve výchozím nastavení, pokud je zjištěna poškozená zpráva.  
  
 **Otázka:** existují zprávy ve frontě, ale není získávání aktivován mé Web hostovaný ve frontě služby. Proč?  
  
 **Odpověď:** nejběžnějším důvodem bývá oprávnění.  
  
1.  Ujistěte se, že `NetMsmqActivator` proces spuštěný a identita `NetMsmqActivator` proces je zadána pro čtení a hledat oprávnění pro frontu.  
  
2.  Pokud `NetMsmqActivator` je monitorování front ve vzdáleném počítači, ujistěte se, že `NetMsmqActivator` není spuštěn pod token s omezeným přístupem. Ke spuštění `NetMsmqActivator` s neomezenou token:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Problémy se zabezpečením související webové hostitelem naleznete: [Webhosting aplikace zařazené do fronty](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **Otázka:** co je nejjednodušší způsob, jak relace přístup?  
  
 **Odpověď:** nastavení automatického dokončování =`true` na operaci, která odpovídá na poslední zprávy v relaci a nastavit automatické dokončování =`false` na všechny zbývající operace služby.  
  
 **Otázka:** kde na MSMQ najdete odpovědi na časté otázky?  
  
 **Odpověď:** Další informace o MSMQ najdete v tématu [služby Řízení front zpráv Microsoft](http://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **Otázka:** Proč mé služby throw `ProtocolException` při čtení z fronty, která obsahuje oba relace zpráv zařazených do fronty a datagram zpráv zařazených do fronty?  
  
 **Odpověď:** je zásadní rozdíl ve zprávách relace způsobem zařazených do fronty a zprávy ve frontě datagram se skládá. Z toho důvodu služba, která očekává ke čtení zprávy ve frontě relace nemůže přijmout zprávu ve frontě datagram a služba byla očekávána ke čtení zprávy ve frontě datagram nemůže přijmout zprávu relace. Při čtení oba typy zpráv ze stejné fronty vyvolá následující výjimky:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Fronty nedoručených zpráv systému, stejně jako všechny vlastní frontu nedoručených zpráv, je zvláště náchylné k tomuto problému, pokud aplikace odešle relace zpráv zařazených do fronty i datagram zpráv ze stejného počítače zařazených do fronty. Pokud nelze úspěšně odeslat zprávu, je přesunuta do fronty nedoručených zpráv. Za těchto okolností je možné, že relace a datagram zprávy do fronty nedoručených zpráv. Neexistuje žádný způsob, jak jednotlivé oba typy zpráv za běhu, při čtení z fronty, proto by neměly odesílat aplikace relace zpráv zařazených do fronty i datagram zpráv ze stejného počítače zařazených do fronty.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integrace MSMQ: Řešení konkrétních potíží  
 **Otázka:** při odeslání zprávy nebo při otevření hostitele služby, zobrazí chybu, která určuje schéma je nesprávný. Proč?  
  
 **Odpověď:** při použití vazby služby MSMQ integrace, je nutné použít schéma msmq.formatname. Například msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Ale když zadáte vlastní frontu nedoručených zpráv, je nutné použít schéma net.msmq.  
  
 **Otázka:** kdy použít název formátu veřejných nebo privátních a otevření hostitele služby na [!INCLUDE[wv](../../../../includes/wv-md.md)], zobrazí chybová zpráva. Proč?  
  
 **Odpověď:** [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] integrace kanál na [!INCLUDE[wv](../../../../includes/wv-md.md)] kontroluje, pokud lze otevřít dílčí fronty pro hlavní aplikace fronty pro zpracování poškozených zpráv. Název dílčí fronta je odvozená od msmq.formatname URI předán do naslouchací proces. Název dílčí fronty služby MSMQ lze pouze přímého názvu formátu. Proto se zobrazí chyba. Změňte na přímého názvu formátu fronty identifikátor URI.  
  
 **Otázka:** při přijímání zprávy z aplikace služby MSMQ, zpráva umístěné ve frontě a není určen ke čtení přijímací [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Proč?  
  
 **Odpověď:** zkontrolujte, zda zpráva má text. Pokud zpráva nemá žádné body, integrace služby MSMQ ignoruje zprávy. Implementace `IErrorHandler` informováni o výjimky a zkontrolujte trasování.  
  
### <a name="security-related-troubleshooting"></a>Řešení potíží souvisejících se zabezpečením  
 **Otázka:** při spuštění vzorku, který používá výchozí vazbu v režimu pracovní skupiny, se zdá, že získat odeslané zprávy, ale nepřijímají příjemce.  
  
 **Odpověď:** ve výchozím nastavení, jsou zprávy podepsané pomocí vnitřního certifikátu služby MSMQ, které vyžaduje adresářové služby Active Directory. V režimu pracovní skupiny protože služba Active Directory není k dispozici, podpis zprávy selže. Proto pojmenováváme zprávy do fronty nedoručených zpráv a je zjištěn příčinu selhání, jako je například "Chybný podpis".  
  
 Chcete-li vypnout zabezpečení je alternativní řešení. To se provádí nastavením <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> ke spolupráci v režimu pracovní skupiny.  
  
 Jiným řešením je získat <xref:System.ServiceModel.MsmqTransportSecurity> z <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> vlastnost a nastavte ji na <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>a nastavte certifikát klienta.  
  
 Ještě jiným řešením je instalace služby MSMQ pomocí integrace služby Active Directory.  
  
 **Otázka:** při odeslání zprávy s vazbou výchozí (přenosu zabezpečení zapnutý) ve službě Active Directory do fronty, se zobrazí zpráva "vnitřní certifikát nebyl nalezen.". Jak tento problém odstranit?  
  
 **Odpověď:** to znamená, že certifikát ve službě Active Directory pro odesílatele musí obnovit. Chcete-li to provést, otevřete **ovládací panely**, **nástroje pro správu**, **Správa počítače**, klikněte pravým tlačítkem na **MSMQ**a vyberte **Vlastnosti**. Vyberte **uživatelský certifikát** a klikněte **obnovení** tlačítko.  
  
 **Otázka:** při odeslání zprávy pomocí <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> a určete certifikát, který chcete použít, se zobrazí zpráva "Neplatný certifikát". Jak tento problém odstranit?  
  
 **Odpověď:** úložiště certifikátů místního počítače nelze použít s režimem certifikátu. Budete muset zkopírovat certifikát z úložiště certifikátů počítače do úložiště aktuálního uživatele pomocí modulu snap-in certifikátů. K získání certifikátu modul snap-in:  
  
1.  Klikněte na tlačítko **spustit**, vyberte **spustit**, typ `mmc`a klikněte na tlačítko **OK**.  
  
2.  V **konzoly Microsoft Management Console**, otevřete **soubor** nabídku a vyberte **přidat nebo odebrat modul Snap-in**.  
  
3.  V **přidat nebo odebrat modul Snap-in** dialogové okno, klikněte **přidat** tlačítko.  
  
4.  V **přidat samostatný modul Snap-in** dialogové okno, vyberte certifikáty a klikněte na tlačítko **přidat**.  
  
5.  V **certifikáty** modul snap-in dialogové okno, vyberte **uživatelským účtem** a klikněte na tlačítko **Dokončit**.  
  
6.  Dál přidejte druhý certifikátů modulu snap-in podle předchozích kroků, ale tentokrát vyberte **účet počítače** a klikněte na tlačítko **Další**.  
  
7.  Vyberte **místního počítače** a klikněte na tlačítko **Dokončit**. Teď můžete přetáhnout a vyřadit certifikáty z úložiště certifikátů počítače do úložiště aktuálního uživatele.  
  
 **Otázka:** při mé služby přečte z fronty na jiný počítač v režimu pracovní skupiny, zobrazí výjimku "přístup byl odepřen".  
  
 **Odpověď:** v režimu pracovní skupiny, pro vzdálené aplikace k získání přístupu k frontě, aplikace musí mít oprávnění k přístupu k frontě. Přidání "Anonymní přihlášení" do fronty seznam řízení přístupu (ACL) a dejte mu oprávnění ke čtení.  
  
 **Otázka:** při síťové služby klienta (nebo libovolného klienta, který nemá účet domény) odešle zprávu ve frontě, odesílání selže s neplatným certifikátem. Jak tento problém odstranit?  
  
 **Odpověď:** Zkontrolujte konfiguraci vazby. Výchozí vazby má zabezpečení služby MSMQ přenosu zapnuté k podepsání zprávy. Vypněte jej.  
  
### <a name="remote-transacted-receives"></a>Obdrží vzdálené transakční  
 **Otázka:** při v počítači A jsou fronty a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která čte zprávy z fronty na počítači zprávy B (vzdálený transakční příjem scénář), nejsou číst zprávy z fronty. Informace o trasování označuje je přijetí se nezdařilo s zpráva "transakci nelze importovat." Jak tento problém lze vyřešit?  
  
 **Odpověď:** existují tři možné důvody:  
  
-   Pokud jste v režimu domény, zobrazí vzdálené transakční vyžaduje přístup k síti Microsoft Distributed Transaction Coordinator služba MSDTC (). Můžete povolit pomocí **přidat nebo odebrat součásti**.  
  
     ![Povolení síťového přístupu](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   Zkontrolujte režim ověřování pro komunikaci se službou Správce transakcí. Pokud jste v režimu pracovní skupiny, musí být vybrána "Ověření nevyžadováno". Pokud jste v režimu domény, musí být vybrán "Vyžaduje vzájemné ověřování".  
  
     ![Povolit transakce XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   Ujistěte se, že služba MSDTC je v seznamu výjimek v **Brána Firewall pro připojení k Internetu** nastavení.  
  
-   Ujistěte se, že používáte [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje vzdálené zpracovaných pro čtení. MSMQ na starších verzích systému Windows nepodporuje vzdálené zpracovaných pro čtení.  
  
 **Otázka:** při čtení z fronty služby je účet network service, například v webového hostitele, proč se zobrazila výjimku odepření přístupu se vyvolá při čtení z fronty?  
  
 **Odpověď:** síťový přístup pro čtení služby musí být přidaný do fronty seznam ACL k zajištění, že síťové služby může ke čtení z fronty.  
  
 **Otázka:** můžete použít službu Aktivace MSMQ k aktivaci aplikace na základě zpráv ve frontě na vzdáleném počítači?  
  
 **Odpověď:** Ano. K tomu, musíte konfigurovat službu Aktivace služby MSMQ pro spuštění jako služba sítě a přidat přístup k síti služby do fronty ve vzdáleném počítači.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Pomocí služby MSMQ vlastní vazby s třídou ReceiveContext povoleno  
 Při použití vlastní vazby služby MSMQ s <xref:System.ServiceModel.Channels.ReceiveContext> povoleno zpracování příchozí zprávy bude používat vlákno fondu vláken, protože nativní MSMQ nepodporuje doplňování vstupně-výstupních operací pro asynchronní <xref:System.ServiceModel.Channels.ReceiveContext> obdrží. Důvodem je, že zpracování takové zprávy používá interní transakce pro <xref:System.ServiceModel.Channels.ReceiveContext> a MSMQ nepodporuje asynchronní zpracování. Chcete-li vyřešit tento problém, můžete přidat <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> ke koncovému bodu můžete vynutit synchronní zpracování, nebo nastavte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> na 1.
