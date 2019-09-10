---
title: Vlastní token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c3c6cfd9d1742f7e839d7b40220792ba455d7673
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855520"
---
# <a name="custom-token"></a><span data-ttu-id="96982-102">Vlastní token</span><span class="sxs-lookup"><span data-stu-id="96982-102">Custom Token</span></span>

<span data-ttu-id="96982-103">Tento příklad ukazuje, jak přidat vlastní implementaci tokenu do aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="96982-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="96982-104">V příkladu se používá `CreditCardToken` k zabezpečenému předávání informací o kreditních kartách klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="96982-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="96982-105">Token se předává v hlavičce zprávy WS-Security a je podepsaný a zašifrovaný pomocí elementu symetrického vazby zabezpečení spolu s textem zprávy a dalšími záhlavími zpráv.</span><span class="sxs-lookup"><span data-stu-id="96982-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="96982-106">To je užitečné v případech, kdy vestavěné tokeny nejsou dostatečné.</span><span class="sxs-lookup"><span data-stu-id="96982-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="96982-107">Tato ukázka předvádí, jak zadat vlastní token zabezpečení pro službu namísto použití jednoho z vestavěných tokenů.</span><span class="sxs-lookup"><span data-stu-id="96982-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="96982-108">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="96982-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="96982-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="96982-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="96982-110">Pro Shrnutí Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="96982-110">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="96982-111">Jak může klient předat službě vlastní token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-111">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="96982-112">Jak může služba spotřebovávat a ověřit vlastní token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-112">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="96982-113">Jak může kód služby WCF získat informace o přijatých tokenech zabezpečení včetně vlastního tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="96982-114">Způsob, jakým se používá certifikát X. 509 serveru k ochraně symetrického klíče použitého pro šifrování a podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="96982-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="96982-115">Ověřování klientů pomocí vlastního tokenu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="96982-115">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="96982-116">Služba zpřístupňuje jeden koncový bod, který je programově vytvořen `BindingHelper` pomocí `EchoServiceHost` tříd a.</span><span class="sxs-lookup"><span data-stu-id="96982-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="96982-117">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="96982-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="96982-118">Vazba je nakonfigurována s vlastní vazbou pomocí `SymmetricSecurityBindingElement` a. `HttpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="96982-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="96982-119">Tato ukázka nastaví, `SymmetricSecurityBindingElement` aby používala certifikát X. 509 služby k ochraně symetrického klíče během přenosu a aby předával vlastní `CreditCardToken` zprávu v hlavičce zprávy WS-Security jako podepsaný a zašifrovaný token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="96982-120">Chování Určuje pověření služby, které se má použít pro ověřování klientů a také informace o certifikátu služby X. 509.</span><span class="sxs-lookup"><span data-stu-id="96982-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="96982-121">Pro použití tokenu platební karty ve zprávě používá ukázka k poskytnutí této funkce vlastní přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="96982-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="96982-122">Třída pověření služby je umístěna ve `CreditCardServiceCredentials` třídě a je přidána do kolekce chování hostitele služby `EchoServiceHost.InitializeRuntime` v metodě.</span><span class="sxs-lookup"><span data-stu-id="96982-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

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

 <span data-ttu-id="96982-123">Koncový bod klienta je nakonfigurován podobným způsobem jako koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="96982-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="96982-124">Klient používá stejnou `BindingHelper` třídu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="96982-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="96982-125">Zbývající část instalace je umístěna ve `Client` třídě.</span><span class="sxs-lookup"><span data-stu-id="96982-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="96982-126">Klient také nastaví informace, které mají být obsaženy v `CreditCardToken` , a informace o certifikátu X. 509 v instalačním kódu `CreditCardClientCredentials` přidáním instance se správnými daty do kolekce chování koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="96982-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="96982-127">Ukázka používá certifikát X. 509 s názvem subjektu nastaveným na `CN=localhost` jako certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="96982-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="96982-128">Implementace vlastního tokenu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="96982-128">Custom Security Token Implementation</span></span>

 <span data-ttu-id="96982-129">Chcete-li ve službě WCF povolit vlastní token zabezpečení, vytvořte reprezentaci objektu vlastního tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="96982-130">Vzorek má toto vyjádření ve `CreditCardToken` třídě.</span><span class="sxs-lookup"><span data-stu-id="96982-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="96982-131">Reprezentace objektu zodpovídá za uchovávání všech relevantních informací o tokenech zabezpečení a poskytuje seznam klíčů zabezpečení obsažených v tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="96982-132">V takovém případě token zabezpečení platební karty neobsahuje žádný bezpečnostní klíč.</span><span class="sxs-lookup"><span data-stu-id="96982-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="96982-133">V další části se dozvíte, co je potřeba udělat, abyste mohli přenést vlastní token přes kabel a spotřebovat ho pomocí koncového bodu WCF.</span><span class="sxs-lookup"><span data-stu-id="96982-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

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
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="96982-134">Získání vlastního tokenu platební karty do a ze zprávy</span><span class="sxs-lookup"><span data-stu-id="96982-134">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="96982-135">Serializátory tokenů zabezpečení ve službě WCF zodpovídají za vytvoření objektu reprezentace tokenů zabezpečení z XML ve zprávě a vytvoření formuláře XML tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="96982-136">Jsou také zodpovědné za jiné funkce, jako je čtení a zápis identifikátorů klíčů odkazujících na tokeny zabezpečení, ale v tomto příkladu se používá pouze funkce související s tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="96982-137">Pokud chcete povolit vlastní token, musíte implementovat vlastní serializátor tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="96982-138">Tato ukázka používá `CreditCardSecurityTokenSerializer` třídu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="96982-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="96982-139">Ve službě vlastní serializátor přečte formulář XML vlastního tokenu a vytvoří z něj reprezentaci objektu vlastního tokenu.</span><span class="sxs-lookup"><span data-stu-id="96982-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="96982-140">V klientovi `CreditCardSecurityTokenSerializer` třída zapisuje informace obsažené v objektu tokenu zabezpečení reprezentaci do zapisovače XML.</span><span class="sxs-lookup"><span data-stu-id="96982-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

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

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

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
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="96982-141">Jak se vytvářejí třídy zprostředkovatele a ověřovatele ověřovacích dat tokenů</span><span class="sxs-lookup"><span data-stu-id="96982-141">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="96982-142">Pověření klienta a služby jsou zodpovědná za poskytování instance Správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="96982-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="96982-143">Instance Správce tokenů zabezpečení se používá k získání poskytovatelů tokenů, ověřovatelů tokenů a serializátorů tokenů.</span><span class="sxs-lookup"><span data-stu-id="96982-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="96982-144">Poskytovatel tokenů vytvoří objektovou reprezentaci tokenu na základě informací obsažených v pověření klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="96982-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="96982-145">Reprezentace objektu tokenu je pak zapsána do zprávy pomocí serializátoru tokenů (popsaných v předchozí části).</span><span class="sxs-lookup"><span data-stu-id="96982-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="96982-146">Ověřovací data tokenu ověřují tokeny, které dorazí do zprávy.</span><span class="sxs-lookup"><span data-stu-id="96982-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="96982-147">Reprezentace objektu příchozího tokenu je vytvořena serializátorem tokenu.</span><span class="sxs-lookup"><span data-stu-id="96982-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="96982-148">Tato reprezentace objektu je pak předána ověřovateli tokenu k ověření.</span><span class="sxs-lookup"><span data-stu-id="96982-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="96982-149">Po úspěšném ověření tokenu vrátí ověřovatel token kolekci `IAuthorizationPolicy` objektů, které reprezentují informace obsažené v tokenu.</span><span class="sxs-lookup"><span data-stu-id="96982-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="96982-150">Tyto informace se používají později během zpracování zprávy k provedení autorizačních rozhodnutí a k poskytování deklarací identity pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96982-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="96982-151">V tomto příkladu používá `CreditCardTokenAuthorizationPolicy` ověřovací data tokenu kreditní karty k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="96982-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="96982-152">Serializátor tokenu zodpovídá za získání reprezentace objektu tokenu do a z tohoto drátu.</span><span class="sxs-lookup"><span data-stu-id="96982-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="96982-153">Tento popis je popsaný v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="96982-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="96982-154">V této ukázce používáme poskytovatele tokenů pouze v klientech a ověřovateli tokenů pouze ve službě, protože chceme přenést token kreditní karty pouze ve směru od klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="96982-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="96982-155">Funkce klienta se nachází v `CreditCardClientCredentials` `CreditCardClientCredentialsSecurityTokenManager` třídách a `CreditCardTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="96982-155">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="96982-156">Ve službě se funkce `CreditCardServiceCredentials`nachází v třídách `CreditCardTokenAuthenticator` , `CreditCardServiceCredentialsSecurityTokenManager`a `CreditCardTokenAuthorizationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="96982-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

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
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
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
                throw new ArgumentNullException(nameof(creditCardInfo));

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
                throw new ArgumentNullException(nameof(creditCardFile));

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
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
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
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
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
                throw new ArgumentNullException(nameof(issuedClaims));
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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="96982-157">Zobrazení informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="96982-157">Displaying the Callers' Information</span></span>

 <span data-ttu-id="96982-158">Chcete-li zobrazit informace o volajícím, `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` použijte, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="96982-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="96982-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizační deklarace přidružené k aktuálnímu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="96982-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="96982-160">Deklarace identity jsou dodány `CreditCardToken` třídou ve své `AuthorizationPolicies` kolekci.</span><span class="sxs-lookup"><span data-stu-id="96982-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

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

 <span data-ttu-id="96982-161">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="96982-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="96982-162">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="96982-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="96982-163">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="96982-163">Setup Batch File</span></span>

 <span data-ttu-id="96982-164">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení založené na certifikátech serveru.</span><span class="sxs-lookup"><span data-stu-id="96982-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="96982-165">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="96982-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="96982-166">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="96982-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="96982-167">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="96982-167">Creating the server certificate:</span></span>

     <span data-ttu-id="96982-168">Následující řádky ze `Setup.bat` souboru Batch vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="96982-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="96982-169">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="96982-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="96982-170">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="96982-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="96982-171">Výchozí hodnota v tomto dávkovém souboru je localhost.</span><span class="sxs-lookup"><span data-stu-id="96982-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="96982-172">Změníte-li `%SERVER_NAME%` proměnnou, je nutné projít soubory Client.cs a Service.cs a nahradit všechny instance místního hostitele názvem serveru, který používáte ve skriptu Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="96982-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="96982-173">Certifikát je uložený v osobním úložišti (osobní) v `LocalMachine` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="96982-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="96982-174">Certifikát je uložený v úložišti LocalMachine pro služby hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="96982-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="96982-175">Pro samoobslužné služby byste měli soubor Batch upravit tak, aby ukládal certifikát klienta do umístění úložiště CurrentUser, a to tak, že nahradíte řetězec LocalMachine řetězcem CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="96982-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="96982-176">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="96982-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="96982-177">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="96982-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="96982-178">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="96982-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="96982-179">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="96982-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="96982-180">Aby bylo možné povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěný proces hostovaný službou IIS, udělena příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="96982-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="96982-181">To se provádí v posledních krocích skriptu Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="96982-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
> <span data-ttu-id="96982-182">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="96982-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="96982-183">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="96982-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="96982-184">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="96982-184">To set up and build the sample</span></span>

1. <span data-ttu-id="96982-185">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96982-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="96982-186">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96982-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="96982-187">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="96982-187">To run the sample on the same computer</span></span>

1. <span data-ttu-id="96982-188">Otevřete okno příkazového řádku sady Visual Studio 2012 s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="96982-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="96982-189">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="96982-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="96982-190">Nezapomeňte odebrat certifikáty spuštěním souboru Cleanup. bat po dokončení ukázky.</span><span class="sxs-lookup"><span data-stu-id="96982-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="96982-191">Další ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="96982-191">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="96982-192">Spusťte soubor Client. exe z adresáře client\bin.</span><span class="sxs-lookup"><span data-stu-id="96982-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="96982-193">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="96982-193">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="96982-194">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="96982-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="96982-195">Spuštění ukázky v rámci počítače</span><span class="sxs-lookup"><span data-stu-id="96982-195">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="96982-196">Vytvořte adresář v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="96982-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="96982-197">Zkopírujte programové soubory služby do adresáře služby na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="96982-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="96982-198">Nezapomeňte zkopírovat CreditCardFile. txt; jinak ověřovatel platební karty nemůže ověřit informace o kreditních kartách odeslaných z klienta.</span><span class="sxs-lookup"><span data-stu-id="96982-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="96982-199">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="96982-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="96982-200">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="96982-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="96982-201">Můžete ho vytvořit pomocí Setup. bat, pokud změníte `%SERVER_NAME%` proměnnou na plně kvalifikovaný název počítače, na kterém je služba hostovaná.</span><span class="sxs-lookup"><span data-stu-id="96982-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="96982-202">Všimněte si, že soubor Setup. bat musí být spuštěný ve Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="96982-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="96982-203">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople na klientovi.</span><span class="sxs-lookup"><span data-stu-id="96982-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="96982-204">To je nutné provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="96982-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="96982-205">V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu a místo localhost zadejte plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="96982-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="96982-206">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="96982-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="96982-207">V souboru Client.cs změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="96982-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="96982-208">V souboru Client.cs změňte název subjektu certifikátu X. 509 tak, aby odpovídal plně kvalifikovanému názvu počítače vzdáleného hostitele namísto localhost.</span><span class="sxs-lookup"><span data-stu-id="96982-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="96982-209">V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="96982-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="96982-210">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="96982-210">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="96982-211">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="96982-211">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="96982-212">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="96982-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
