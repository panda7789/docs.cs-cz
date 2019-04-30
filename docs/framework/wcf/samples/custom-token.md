---
title: Vlastní token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: fbde7d1006cabddafa7e03fdee0e3493416001da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855046"
---
# <a name="custom-token"></a>Vlastní token
Tento příklad ukazuje, jak přidat vlastní implementaci token do aplikace Windows Communication Foundation (WCF). V příkladu se používá `CreditCardToken` bezpečně předat informace o kreditní karty klienta ke službě. Token je předán do záhlaví zprávy WS-Security je podepsaný a zašifrovaný pomocí elementu vazby zabezpečení symetrický spolu s textem zprávy a další záhlaví zpráv. To je užitečné v případech, kdy jsou předdefinované tokeny není dostatečná. Tato ukázka předvádí, jak poskytnout vlastní bezpečnostní token pro službu namísto pomocí jedné z předdefinovaných tokeny. Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

 Souhrnně řečeno, tento příklad znázorňuje následující:

- Jak klienta můžete předat vlastní bezpečnostní token do služby.

- Jak službu využívat a ověřit vlastní bezpečnostní token.

- Jak kód služby WCF můžete získat informace o tokeny přijatý zabezpečení včetně vlastní bezpečnostní token.

- Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.

## <a name="client-authentication-using-a-custom-security-token"></a>Pomocí tokenu zabezpečení vlastního ověření klienta
 Služba poskytuje jeden koncový bod, který je prostřednictvím kódu programu vytvořili pomocí `BindingHelper` a `EchoServiceHost` třídy. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována s vlastními vazbami pomocí `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`. Tato ukázka nastaví `SymmetricSecurityBindingElement` chránit symetrický klíč během přenosu a předat vlastní pomocí certifikátu X.509 služby `CreditCardToken` v záhlaví zprávy WS-Security jako token zabezpečení podepsaný a šifrovaná. Chování Určuje přihlašovací údaje služby, které se mají použít pro ověřování klientů a také informace o certifikát služby X.509.

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 Používat platební kartu token ve zprávě, ukázka používá vlastní službu přihlašovací údaje k poskytují tuto funkci. Třída přihlašovací údaje služby se nachází v `CreditCardServiceCredentials` třídy a je přidán do kolekce chování hostitele služby v `EchoServiceHost.InitializeRuntime` metody.

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 Koncový bod klienta je nakonfigurovaný podobným způsobem jako koncový bod služby. Klient používá stejný `BindingHelper` třídy za účelem vytvoření vazby. Zbývající část nastavení se nachází v `Client` třídy. Klient také nastaví informace, které mají být obsažena v `CreditCardToken` a informace o certifikát služby X.509 v instalační kód tak, že přidáte `CreditCardClientCredentials` instance s odpovídající data do kolekce chování koncového bodu klienta. Ukázka používá certifikát X.509 s názvem subjektu nastavit na `CN=localhost` jako certifikát služby.

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// configure the credit card credentials on the channel factory
CreditCardClientCredentials credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// configure the service certificate on the credentials
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// replace ClientCredentials with CreditCardClientCredentials
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine("Echo service returned: {0}", client.Echo());

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>Implementace vlastní bezpečnostní Token
 Povolit vlastní bezpečnostní token ve službě WCF, vytvořte reprezentaci objektu vlastní bezpečnostní token. Ukázka obsahuje tento zápis `CreditCardToken` třídy. Reprezentaci objektu zodpovídá, která uchovává všechny relevantní informace o tokenu zabezpečení a zadat seznam klíčů zabezpečení obsažených v tokenu zabezpečení. Token zabezpečení platební karty v tomto případě neobsahuje klíč zabezpečení.

 Další část popisuje, co musí udělat, aby povolit vlastní token má být přenesen prostřednictvím sítě jako a spotřebovávány koncového bodu WCF.

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException("cardInfo");

        if (id == null)
            throw new ArgumentNullException("id");

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Získání tokenu do a ze zprávy vlastní platební karty
 Serializátory tokenů zabezpečení ve službě WCF zodpovídají za vytváření objektová reprezentace tokeny zabezpečení ze souboru XML ve zprávě a vytvoření XML formuláře tokenů zabezpečení. Zodpovídají také za další funkce, jako je čtení a zápis klíče identifikátory odkazující na tokeny zabezpečení, ale v tomto příkladu pouze související s tokeny funkci zabezpečení. Pokud chcete povolit vlastní token musíte implementovat vlastní serializátoru tokenů zabezpečení. Tento příklad používá `CreditCardSecurityTokenSerializer` třídu pro tento účel.

 Ve službě uživatelský serializátor přečte formulář XML vlastní token a vytvoří reprezentaci objektu vlastní token z něj.

 V klientském počítači `CreditCardSecurityTokenSerializer` třídy zapisuje informace obsažené v reprezentaci objektu tokenu zabezpečení do zapisovače XML.

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;

        else
            return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null) { throw new ArgumentNullException("writer"); }
        if (token == null) { throw new ArgumentNullException("token"); }

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Vytvoření zprostředkovatele tokenu a tokenu třídy Authenticator
 Přihlašovací údaje klient a služba je zodpovědná za poskytování instance Správce tokenů zabezpečení. Instance Správce tokenů zabezpečení slouží k získání poskytovatele tokenů, ověřovací data tokenu a tokenu serializátory.

 Poskytovatel tokenu vytvoří reprezentaci objektu tokenu na základě informací obsažených v přihlašovacích údajů klienta nebo službě. Reprezentace objektu tokenu se poté zapíšou do zprávy pomocí serializátoru tokenů (viz popis v předchozí části).

 Ověřovací data tokenu ověří tokeny, které budou doručeny do zprávy. Příchozí token objektová reprezentace je vytvořen pomocí serializátoru tokenů. Tento zápis objekt je pak předán ověřovací data tokenu pro ověření. Po úspěšném ověření tokenu ověřovací data tokenu vrátí kolekci `IAuthorizationPolicy` objekty, které představují informací obsažených v tokenu. Tyto informace slouží později během zpracování zpráv a provádění rozhodování o autorizaci poskytovat deklarace identity pro aplikace. V tomto příkladu se používá ověřovací data tokenu platební karty `CreditCardTokenAuthorizationPolicy` pro tento účel.

 Token serializátor je zodpovědná za získání tokenu do a z přenosu reprezentaci objektu. Tento postup je popsán v předchozí části.

 V této ukázce používáme zprostředkovatele tokenu pouze na klienta a ověřovací data tokenu pouze na služby, protože chceme, aby přenášet platební karty token pouze ve směru klient služba.

 Funkce na straně klienta se nachází v `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` a `CreditCardTokenProvider` třídy.

 Ve službě, se funkce nachází v `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` a `CreditCardTokenAuthorizationPolicy` třídy.

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException("creditCardInfo");

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // handle this token for Custom
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // return server cert
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
            {
                throw new ArgumentNullException("creditCardInfo");
            }
            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException("creditCardFile");

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException("issuedClaims");
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a>Zobrazení informací o volajícím.
 K zobrazení informací volajícího, použijte `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím ukázkovém kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizaci deklarací identity přidružené k aktuální volajícího. Deklarace identity jsou poskytována `CreditCardToken` třídy v jeho `AuthorizationPolicies` kolekce.

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.

 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.

- Vytváří se certifikát serveru:

     Následující řádky z `Setup.bat` dávkový soubor vytvořte certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnné Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tomto souboru batch výchozí hodnota je localhost. Pokud změníte `%SERVER_NAME%` proměnné, musíte projít Client.cs a Service.cs soubory a nahraďte všechny výskyty místního hostitele s názvem serveru, který používáte v skript Setup.bat.

     Certifikát je uložen v úložišti (osobních) v části `LocalMachine` umístění úložiště. Certifikát je uložen v úložišti LocalMachine pro služby hostované v IIS. V místním prostředí služby upravte dávkový soubor pro uložení certifikátu klienta v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:

     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Povolit přístup k privátnímu klíči certifikátu ze služby hostované v IIS, musíte uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělena příslušná oprávnění pro privátní klíč. Toho lze dosáhnout poslední kroky v skript Setup.bat.

    ```
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.

#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku

1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1. Otevřete okno příkazového řádku sady Visual Studio 2012 s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.

> [!NOTE]
>  Je potřeba certifikáty odebrat spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
1. Spusťte Client.exe z client\bin adresáře. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
2. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computer"></a>Ke spuštění ukázky napříč počítači  
  
1. Vytvoření adresáře na počítači se službou pro binární soubory služby.  
  
2. Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou. Nezapomeňte zkopírovat CreditCardFile.txt; v opačném případě authenticator platební karty nelze ověřit informace o platební kartě odeslaných z klienta. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Můžete si ho pomocí Setup.bat změníte-li vytvořit `%SERVER_NAME%` proměnné pro plně kvalifikovaný název počítače, který je hostitelem služby. Všimněte si, že se soubor Setup.bat musí být spuštěn v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople na straně klienta. Musíte to provést jenom v případě, že certifikát serveru není vystavený důvěryhodného vystavitele.  
  
5. V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu k zadání názvu počítače plně kvalifikovaný, místo localhost.  
  
6. Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
7. V souboru Client.cs změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
8. V souboru Client.cs změňte název subjektu certifikátu X.509 služby tak, aby odpovídala plně kvalifikovaný název vzdáleného hostitele, místo localhost.  
  
9. Na klientském počítači spusťte Client.exe z okna příkazového řádku.  
  
10. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1. Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
