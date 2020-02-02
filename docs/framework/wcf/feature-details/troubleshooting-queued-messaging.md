---
title: Řešení potíží se zasíláním zpráv zařazovaných do front
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 5c039c34983647884561f33645f26e4a89280248
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921272"
---
# <a name="troubleshooting-queued-messaging"></a>Řešení potíží se zasíláním zpráv zařazovaných do front

Tato část obsahuje nejčastější dotazy a pomoc při odstraňování potíží s používáním front v Windows Communication Foundation (WCF).

## <a name="common-questions"></a>Běžné dotazy

**Otázka:** Použil (a) jsem WCF beta 1 a nainstaloval (a) opravu hotfix služby MSMQ. Musím tuto opravu hotfix odebrat?

**Odpověď:** Ano. Tato oprava hotfix již není podporována. WCF teď funguje v MSMQ bez požadavku na opravu hotfix.

**Otázka:** Existují dvě vazby pro službu MSMQ: <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Co mám použít a kdy?

**A:** Použijte <xref:System.ServiceModel.NetMsmqBinding>, pokud chcete použít službu MSMQ jako přenos pro komunikaci ve frontě mezi dvěma aplikacemi WCF. Použijte <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>, pokud chcete použít existující aplikace služby MSMQ ke komunikaci s novými aplikacemi WCF.

**Otázka:** Je potřeba upgradovat službu MSMQ, aby používala vazby <xref:System.ServiceModel.NetMsmqBinding> a `MsmqIntegration`?

**Odpověď:** Ne. Obě vazby fungují s MSMQ 3,0 v systémech Windows XP a Windows Server 2003. Při upgradu na službu MSMQ 4,0 v systému Windows Vista budou některé funkce vazeb dostupné.

**Otázka:** Jaké funkce <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> vazby jsou k dispozici ve službě MSMQ 4,0, ale ne v MSMQ 3,0?

**A:** Ve službě MSMQ 4,0 jsou k dispozici následující funkce, které nejsou ve službě MSMQ 3,0:

- Vlastní fronta nedoručených zpráv je podporována pouze ve službě MSMQ 4,0.

- MSMQ 3,0 a 4,0 zpracovávají poškozené zprávy různě.

- Pouze služba MSMQ 4,0 podporuje vzdálené čtení v transakčním režimu.

Další informace najdete v tématu [rozdíly ve funkcích služby Řízení front v systémech Windows Vista, Windows Server 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).

**Otázka:** Můžu použít MSMQ 3,0 na jedné straně komunikace ve frontě a MSMQ 4,0 na druhé straně?

**Odpověď:** Ano.

**Otázka:** Chci integrovat stávající aplikace služby MSMQ s novými klienty nebo servery WCF. Potřebuji upgradovat obě strany infrastruktury služby MSMQ?

**Odpověď:** Ne. Nemusíte upgradovat na žádnou stranu na službu MSMQ 4,0.

## <a name="troubleshooting"></a>Odstraňování problémů

Tato část obsahuje odpovědi na nejčastější problémy při odstraňování potíží. Některé problémy, které jsou známá omezením, jsou popsány také v poznámkách k verzi.

**Otázka:** Snažím se použít soukromou frontu a zobrazí se tato výjimka: `System.InvalidOperationException`: adresa URL je neplatná. Adresa URL pro frontu nesmí obsahovat znak $. Použijte syntaxi na adrese NET. MSMQ://machine/private/queueName a vyřešte soukromou frontu.

**A:** V konfiguraci a kódu prosím zkontrolujte identifikátor URI ve frontě. Nepoužívejte v identifikátoru URI znak "$". Pokud například chcete adresovat soukromou frontu s názvem OrdersQueue, zadejte identifikátor URI as NET. MSMQ://localhost/private/ordersQueue.

**Otázka:** Volání `ServiceHost.Open()` v naší aplikaci ve frontě vyvolá následující výjimku: `System.ArgumentException`: základní adresa nesmí obsahovat řetězec dotazu identifikátoru URI. Proč?

**A:** Ověřte identifikátor URI fronty v konfiguračním souboru a ve vašem kódu. I když fronty MSMQ podporují použití znaku "?", identifikátory URI interpretují tento znak jako začátek řetězcového dotazu. Chcete-li se tomuto problému vyhnout, použijte názvy front, které neobsahují znaky?.

**Otázka:** Moje odeslání bylo úspěšné, ale na přijímači není vyvolána žádná operace služby. Proč?

**A:** K určení odpovědi můžete použít následující kontrolní seznam:

- Ověřte, zda jsou požadavky transakční fronty kompatibilní se zadanými zárukami. Všimněte si následujících zásad:

  - Můžete odesílat trvalé zprávy (datagramy a relace) s "právě jednou" ujištění (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) pouze do transakční fronty.

  - Relace můžete odesílat pouze pomocí ujištění "právě jednou".

  - Aby bylo možné přijímat zprávy v relaci z transakční fronty, je nutné zadat transakci.

  - Můžete odesílat nebo přijímat nestálé nebo trvalé zprávy (pouze datagramy) bez ujištění (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) pouze do netransakční fronty.

- Ověřte frontu nedoručených zpráv. Pokud se zde nacházejí zprávy, určete, proč nebyly dodány.

- Podívejte se na odchozí fronty pro připojení nebo problémy s adresou.

**Otázka:** Zadal jsem vlastní frontu nedoručených zpráv, ale při spuštění aplikace odesílatele se zobrazí výjimka, že buď nebyla nalezena fronta nedoručených zpráv, nebo odesílající aplikace nemá oprávnění ke frontě nedoručených zpráv. Proč se to děje?

**A:** Vlastní identifikátor URI fronty nedoručených zpráv musí zahrnovat "localhost" nebo název počítače v prvním segmentu, například NET. MSMQ://localhost/private/myAppdead-letter Queue.

**Otázka:** Je vždycky potřeba definovat vlastní frontu nedoručených zpráv, nebo má výchozí frontu nedoručených zpráv?

**A:** Pokud jsou záruky "právě jednou" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a pokud nezadáte vlastní frontu nedoručených zpráv, výchozí hodnota je fronta nedoručených transakčních zpráv v rámci systému.

Pokud jsou záruky žádné (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), není ve výchozím nastavení žádná funkce fronty nedoručených zpráv.

**Otázka:** Moje služba vyvolá v procesu SvcHost. Open se zprávou "požadavky na EndpointListener nelze splnit rozhraním ListenerFactory". Proč?

A. Podívejte se na kontrakt služby. Možná jste zapomněli do všech operací služby umístit "IsOneWay =`true`". Fronty podporují pouze jednosměrné operace služby.

**Otázka:** Ve frontě jsou zprávy, ale není vyvolána žádná operace služby. Jaký je problém?

**A:** Zjistěte, jestli hostitel služby selhal. Můžete se podívat na trasování nebo implementaci `IErrorHandler`. Selhání hostitele služby ve výchozím nastavení, pokud je zjištěna nezpracovatelná zpráva.

**Otázka:** Ve frontě jsou zprávy, ale moje služba hostovaná ve frontě web není aktivovaná. Proč?

**A:** Nejběžnějším důvodem jsou oprávnění.

1. Zajistěte, aby byl proces `NetMsmqActivator` spuštěný, a identita `NetMsmqActivator` procesu má přidělené oprávnění ke čtení a hledání ve frontě.

2. Pokud `NetMsmqActivator` sleduje fronty na vzdáleném počítači, zajistěte, aby `NetMsmqActivator` neběžely s omezeným tokenem. Spuštění `NetMsmqActivator` s neomezeným tokenem:

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

Problémy webového hostitele nesouvisející se zabezpečením odkazují na: [web hostující aplikaci ve frontě](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).

**Otázka:** Jaký je nejjednodušší způsob, jak získat přístup k relacím?

**A:** Nastavte AutoComplete =`true` u operace, která odpovídá poslední zprávě v relaci, a nastavte automatické dokončování =`false` u všech zbývajících operací služby.

**Otázka:** Proč moje služba při čtení z fronty, která obsahuje obě zprávy relace ve frontě a zprávy datagram zařazená do fronty, vyvolá `ProtocolException`?

**A:** Způsob, jakým se skládají zprávy ve frontě a zprávy datagramů, jsou tvořené zásadním rozdílem. Proto služba, která očekává čtení zprávy ve frontě, nemůže přijmout zprávu datagramu ve frontě a služba, která očekává čtení zprávy datagramu ve frontě, nemůže získat zprávu relace. Při pokusu o čtení obou typů zpráv ze stejné fronty je vyvolána následující výjimka:

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

Fronta nedoručených zpráv systému, stejně jako jakákoli vlastní fronta nedoručených zpráv, je obzvláště náchylná k tomuto problému, pokud aplikace odesílá zprávy relace ve frontě i zprávy datagram ve stejném počítači. Pokud zprávu nelze úspěšně odeslat, bude přesunuta do fronty nedoručených zpráv. Za těchto okolností je možné mít ve frontě nedoručených zpráv obě relace i datagram. Neexistuje žádný způsob, jak při čtení z fronty oddělit oba typy zpráv za běhu, proto by aplikace neměly odesílat obě zprávy relací ve frontě a zprávy datagram ze stejného počítače.

### <a name="msmq-integration-specific-troubleshooting"></a>Integrace služby MSMQ: konkrétní řešení potíží

**Otázka:** Při odeslání zprávy nebo při otevření hostitele služby se zobrazí chyba, která indikuje, že je schéma chybné. Proč?

**A:** Při použití vazby integrace služby MSMQ je nutné použít schéma MSMQ. FormatName. Například MSMQ. FormatName: DIRECT = OS: .\private $ \OrdersQueue. Když ale zadáte vlastní frontu nedoručených zpráv, musíte použít schéma NET. MSMQ.

**Otázka:** Když používám název veřejného nebo privátního formátu a v systému Windows Vista se otevře hostitel služby, zobrazí se chybová zpráva. Proč?

**A:** Kanál pro integraci WCF v systému Windows Vista kontroluje, zda lze otevřít podfrontu pro hlavní frontu aplikace pro zpracování nezpracovatelných zpráv. Název podfronty je odvozen z identifikátoru URI služby MSMQ. FormatName předaného do naslouchacího procesu. Název podfronty v MSMQ může být pouze název přímého formátu. Zobrazí se chyba. Změňte identifikátor URI fronty na název přímého formátu.

**Otázka:** Při příjmu zprávy z aplikace služby MSMQ se zpráva nachází ve frontě a není přečtena přijímající aplikací WCF. Proč?

**A:** Zkontrolujte, zda zpráva obsahuje tělo. Pokud zpráva neobsahuje žádné tělo, kanál integrace služby MSMQ zprávu ignoruje. Implementujte `IErrorHandler` pro oznamování výjimek a kontrolu trasování.

### <a name="security-related-troubleshooting"></a>Řešení potíží souvisejících se zabezpečením

**Otázka:** Po spuštění ukázky, která používá výchozí vazbu v režimu pracovní skupiny, se zprávy jeví jako odesílané, ale příjemce je nikdy neobdrží.

**A:** Ve výchozím nastavení se zprávy podepisují pomocí interního certifikátu služby MSMQ, který vyžaduje adresářovou službu Active Directory. V režimu pracovní skupiny, protože služba Active Directory není k dispozici, podepisování zprávy se nezdařilo. Proto je uvedena zpráva ve frontě nedoručených zpráv a příčině selhání, jako je například "chybný podpis".

Alternativním řešením je vypnout zabezpečení. Můžete to udělat nastavením <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None>, aby fungovalo v režimu pracovní skupiny.

Dalším řešením je získat <xref:System.ServiceModel.MsmqTransportSecurity> z vlastnosti <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> a nastavit ji na <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>a nastavit klientský certifikát.

Ještě dalším řešením je instalace služby MSMQ s integrací služby Active Directory.

**Otázka:** Když pošlu zprávu s výchozí vazbou (zapnuté zabezpečení přenosu) ve službě Active Directory do fronty, zobrazí se zpráva "interní certifikát nebyl nalezen". Návody opravit?

**A:** To znamená, že certifikát ve službě Active Directory pro odesílatele musí být obnoven. Provedete to tak, že otevřete **Ovládací panely**, **Nástroje pro správu**, **Správa počítače**, kliknete pravým tlačítkem myši na položku **MSMQ**a vyberete možnost **vlastnosti**. Vyberte kartu **certifikát uživatele** a klikněte na tlačítko **obnovit** .

**Otázka:** Když pošlu zprávu pomocí <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> a určíte certifikát, který se má použít, zobrazí se zpráva "Neplatný certifikát". Návody opravit?

**A:** Nemůžete použít úložiště certifikátů místního počítače s režimem certifikátu. Je nutné zkopírovat certifikát z úložiště certifikátů počítače do úložiště s aktuálním uživatelem pomocí modulu snap-in Certifikáty. Získání modulu snap-in certifikáty:

1. Klikněte na tlačítko **Start**, vyberte možnost **Spustit**, zadejte příkaz `mmc`a klikněte na tlačítko **OK**.

2. V **konzole Microsoft Management Console**otevřete nabídku **soubor** a vyberte možnost **Přidat nebo odebrat modul snap-in**.

3. V dialogovém okně **Přidat nebo odebrat modul snap-in** klikněte na tlačítko **Přidat** .

4. V dialogovém okně **Přidat samostatný modul snap-in** vyberte certifikáty a klikněte na **Přidat**.

5. V dialogovém okně modul snap-in **certifikáty** vyberte **Můj uživatelský účet** a klikněte na **Dokončit**.

6. V dalším kroku přidejte další modul snap-in certifikáty pomocí předchozích kroků, ale tentokrát vyberte **účet počítače** a klikněte na **Další**.

7. Vyberte **místní počítač** a klikněte na **Dokončit**. Nyní můžete přetahovat certifikáty z úložiště certifikátů počítače do aktuálního úložiště uživatele.

**Otázka:** Když moje služba načte z fronty v jiném počítači v režimu pracovní skupiny, zobrazí se výjimka "přístup byl odepřen".

**A:** V režimu pracovní skupiny, aby Vzdálená aplikace získala přístup do fronty, aplikace musí mít oprávnění pro přístup do fronty. Přidejte do seznamu řízení přístupu (ACL) fronty možnost anonymní přihlášení a udělte jí oprávnění ke čtení.

**Otázka:** Když klient síťové služby (nebo jakýkoli klient, který nemá účet domény) odešle zprávu ve frontě, odeslání se nezdařila s neplatným certifikátem. Návody opravit?

**A:** Ověřte konfiguraci vazby. Výchozí vazba má zapnuté zabezpečení přenosu MSMQ pro podepsání zprávy. Vypnout.

### <a name="remote-transacted-receives"></a>Vzdáleně transakční příjem

**Otázka:** Když mám frontu na počítači a a službu WCF, která čte zprávy z fronty v počítači B (scénář vzdáleného příjmu v provozu), zprávy se z fronty nečtou. Trasovací informace indikují, že se příjem nezdařil, zpráva "transakce nemůže být importována". Co můžete dělat na tento problém vyřešit?

**A:** Existují tři možné příčiny:

- Pokud pracujete v režimu domény, vzdálené transakční přijímání vyžaduje přístup k síti Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Tuto možnost můžete povolit pomocí **Přidat nebo odebrat součásti**.

  ![Snímek obrazovky, který ukazuje povolení přístupu k síti DTC.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- Ověřte režim ověřování pro komunikaci se správcem transakcí. Pokud pracujete v režimu pracovní skupiny, je nutné vybrat možnost bez vyžadování ověřování. Pokud jste v režimu domény, musíte vybrat možnost vzájemného ověřování.

  ![Povolování transakcí XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")

- Ujistěte se, že je MSDTC v seznamu výjimek v nastavení **brány firewall pro připojení k Internetu** .

- Ujistěte se, že používáte systém Windows Vista. Služba MSMQ v systému Windows Vista podporuje vzdálené čtení v transakčním režimu. Funkce MSMQ ve starších verzích Windows nepodporuje vzdálené čtení v režimu Transact.

**Otázka:** Když je služba čtena z fronty jako síťová služba, například na webovém hostiteli, proč se při čtení z fronty vyvolá výjimka odepření přístupu?

**A:** Přístup ke čtení síťové služby musí být přidán do seznamu ACL fronty, aby bylo zajištěno, že síťová služba bude moci číst z fronty.

**Otázka:** Můžu pomocí aktivační služby MSMQ aktivovat aplikace na základě zpráv ve frontě ve vzdáleném počítači?

**Odpověď:** Ano. K tomu je nutné nakonfigurovat aktivační službu MSMQ tak, aby běžela jako síťová služba, a do fronty ve vzdáleném počítači přidat přístup k síťové službě.

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Použití vlastních vazeb MSMQ s povoleným kontextem ReceiveContext

Když použijete vlastní vazbu služby MSMQ s povoleným <xref:System.ServiceModel.Channels.ReceiveContext>m, příchozí zpráva bude používat vlákno fondu vláken, protože nativní služba MSMQ nepodporuje doplňování vstupu a výstupu pro asynchronní <xref:System.ServiceModel.Channels.ReceiveContext> přijímání. Důvodem je to, že zpracování takové zprávy používá interní transakce pro <xref:System.ServiceModel.Channels.ReceiveContext> a služba MSMQ nepodporuje asynchronní zpracování. Pokud chcete tento problém obejít, můžete do koncového bodu přidat <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> pro vynucení synchronního zpracování nebo nastavení <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> na 1.
