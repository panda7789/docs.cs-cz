---
title: Vlastní token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 03a1f8bd6a5f2ec57e7af865d2aadde77b40326d
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261521"
---
# <a name="custom-token"></a><span data-ttu-id="7b47d-102">Vlastní token</span><span class="sxs-lookup"><span data-stu-id="7b47d-102">Custom Token</span></span>
<span data-ttu-id="7b47d-103">Tento příklad ukazuje, jak přidat vlastní implementaci token do aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7b47d-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7b47d-104">V příkladu se používá `CreditCardToken` bezpečně předat informace o kreditní karty klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="7b47d-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="7b47d-105">Token je předán do záhlaví zprávy WS-Security je podepsaný a zašifrovaný pomocí elementu vazby zabezpečení symetrický spolu s textem zprávy a další záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="7b47d-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="7b47d-106">To je užitečné v případech, kdy jsou předdefinované tokeny není dostatečná.</span><span class="sxs-lookup"><span data-stu-id="7b47d-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="7b47d-107">Tato ukázka předvádí, jak poskytnout vlastní bezpečnostní token pro službu namísto pomocí jedné z předdefinovaných tokeny.</span><span class="sxs-lookup"><span data-stu-id="7b47d-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="7b47d-108">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="7b47d-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
>  <span data-ttu-id="7b47d-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7b47d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="7b47d-110">Souhrnně řečeno, tento příklad znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="7b47d-110">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="7b47d-111">Jak klienta můžete předat vlastní bezpečnostní token do služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-111">How a client can pass a custom security token to a service.</span></span>

-   <span data-ttu-id="7b47d-112">Jak službu využívat a ověřit vlastní bezpečnostní token.</span><span class="sxs-lookup"><span data-stu-id="7b47d-112">How the service can consume and validate a custom security token.</span></span>

-   <span data-ttu-id="7b47d-113">Jak kód služby WCF můžete získat informace o tokeny přijatý zabezpečení včetně vlastní bezpečnostní token.</span><span class="sxs-lookup"><span data-stu-id="7b47d-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

-   <span data-ttu-id="7b47d-114">Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7b47d-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="7b47d-115">Pomocí tokenu zabezpečení vlastního ověření klienta</span><span class="sxs-lookup"><span data-stu-id="7b47d-115">Client Authentication Using a Custom Security Token</span></span>
 <span data-ttu-id="7b47d-116">Služba poskytuje jeden koncový bod, který je prostřednictvím kódu programu vytvořili pomocí `BindingHelper` a `EchoServiceHost` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="7b47d-117">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7b47d-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7b47d-118">Je vazba konfigurována s vlastními vazbami pomocí `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="7b47d-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="7b47d-119">Tato ukázka nastaví `SymmetricSecurityBindingElement` chránit symetrický klíč během přenosu a předat vlastní pomocí certifikátu X.509 služby `CreditCardToken` v záhlaví zprávy WS-Security jako token zabezpečení podepsaný a šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="7b47d-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="7b47d-120">Chování Určuje přihlašovací údaje služby, které se mají použít pro ověřování klientů a také informace o certifikát služby X.509.</span><span class="sxs-lookup"><span data-stu-id="7b47d-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```
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

 <span data-ttu-id="7b47d-121">Používat platební kartu token ve zprávě, ukázka používá vlastní službu přihlašovací údaje k poskytují tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="7b47d-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="7b47d-122">Třída přihlašovací údaje služby se nachází v `CreditCardServiceCredentials` třídy a je přidán do kolekce chování hostitele služby v `EchoServiceHost.InitializeRuntime` metody.</span><span class="sxs-lookup"><span data-stu-id="7b47d-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

```
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

 <span data-ttu-id="7b47d-123">Koncový bod klienta je nakonfigurovaný podobným způsobem jako koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="7b47d-124">Klient používá stejný `BindingHelper` třídy za účelem vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="7b47d-125">Zbývající část nastavení se nachází v `Client` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="7b47d-126">Klient také nastaví informace, které mají být obsažena v `CreditCardToken` a informace o certifikát služby X.509 v instalační kód tak, že přidáte `CreditCardClientCredentials` instance s odpovídající data do kolekce chování koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47d-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="7b47d-127">Ukázka používá certifikát X.509 s názvem subjektu nastavit na `CN=localhost` jako certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration
channelFactory =
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

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

## <a name="custom-security-token-implementation"></a><span data-ttu-id="7b47d-128">Implementace vlastní bezpečnostní Token</span><span class="sxs-lookup"><span data-stu-id="7b47d-128">Custom Security Token Implementation</span></span>
 <span data-ttu-id="7b47d-129">Povolit vlastní bezpečnostní token ve službě WCF, vytvořte reprezentaci objektu vlastní bezpečnostní token.</span><span class="sxs-lookup"><span data-stu-id="7b47d-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="7b47d-130">Ukázka obsahuje tento zápis `CreditCardToken` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="7b47d-131">Reprezentaci objektu zodpovídá, která uchovává všechny relevantní informace o tokenu zabezpečení a zadat seznam klíčů zabezpečení obsažených v tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="7b47d-132">Token zabezpečení platební karty v tomto případě neobsahuje klíč zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="7b47d-133">Další část popisuje, co musí udělat, aby povolit vlastní token má být přenesen prostřednictvím sítě jako a spotřebovávány koncového bodu WCF.</span><span class="sxs-lookup"><span data-stu-id="7b47d-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

```
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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="7b47d-134">Získání tokenu do a ze zprávy vlastní platební karty</span><span class="sxs-lookup"><span data-stu-id="7b47d-134">Getting the Custom Credit Card Token to and from the Message</span></span>
 <span data-ttu-id="7b47d-135">Serializátory tokenů zabezpečení ve službě WCF zodpovídají za vytváření objektová reprezentace tokeny zabezpečení ze souboru XML ve zprávě a vytvoření XML formuláře tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="7b47d-136">Zodpovídají také za další funkce, jako je čtení a zápis klíče identifikátory odkazující na tokeny zabezpečení, ale v tomto příkladu pouze související s tokeny funkci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="7b47d-137">Pokud chcete povolit vlastní token musíte implementovat vlastní serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="7b47d-138">Tento příklad používá `CreditCardSecurityTokenSerializer` třídu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="7b47d-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="7b47d-139">Ve službě uživatelský serializátor přečte formulář XML vlastní token a vytvoří reprezentaci objektu vlastní token z něj.</span><span class="sxs-lookup"><span data-stu-id="7b47d-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="7b47d-140">V klientském počítači `CreditCardSecurityTokenSerializer` třídy zapisuje informace obsažené v reprezentaci objektu tokenu zabezpečení do zapisovače XML.</span><span class="sxs-lookup"><span data-stu-id="7b47d-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```
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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="7b47d-141">Vytvoření zprostředkovatele tokenu a tokenu třídy Authenticator</span><span class="sxs-lookup"><span data-stu-id="7b47d-141">How Token Provider and Token Authenticator Classes are Created</span></span>
 <span data-ttu-id="7b47d-142">Přihlašovací údaje klient a služba je zodpovědná za poskytování instance Správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b47d-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="7b47d-143">Instance Správce tokenů zabezpečení slouží k získání poskytovatele tokenů, ověřovací data tokenu a tokenu serializátory.</span><span class="sxs-lookup"><span data-stu-id="7b47d-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="7b47d-144">Poskytovatel tokenu vytvoří reprezentaci objektu tokenu na základě informací obsažených v přihlašovacích údajů klienta nebo službě.</span><span class="sxs-lookup"><span data-stu-id="7b47d-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="7b47d-145">Reprezentace objektu tokenu se poté zapíšou do zprávy pomocí serializátoru tokenů (viz popis v předchozí části).</span><span class="sxs-lookup"><span data-stu-id="7b47d-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="7b47d-146">Ověřovací data tokenu ověří tokeny, které budou doručeny do zprávy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="7b47d-147">Příchozí token objektová reprezentace je vytvořen pomocí serializátoru tokenů.</span><span class="sxs-lookup"><span data-stu-id="7b47d-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="7b47d-148">Tento zápis objekt je pak předán ověřovací data tokenu pro ověření.</span><span class="sxs-lookup"><span data-stu-id="7b47d-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="7b47d-149">Po úspěšném ověření tokenu ověřovací data tokenu vrátí kolekci `IAuthorizationPolicy` objekty, které představují informací obsažených v tokenu.</span><span class="sxs-lookup"><span data-stu-id="7b47d-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="7b47d-150">Tyto informace slouží později během zpracování zpráv a provádění rozhodování o autorizaci poskytovat deklarace identity pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b47d-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="7b47d-151">V tomto příkladu se používá ověřovací data tokenu platební karty `CreditCardTokenAuthorizationPolicy` pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="7b47d-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="7b47d-152">Token serializátor je zodpovědná za získání tokenu do a z přenosu reprezentaci objektu.</span><span class="sxs-lookup"><span data-stu-id="7b47d-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="7b47d-153">Tento postup je popsán v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="7b47d-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="7b47d-154">V této ukázce používáme zprostředkovatele tokenu pouze na klienta a ověřovací data tokenu pouze na služby, protože chceme, aby přenášet platební karty token pouze ve směru klient služba.</span><span class="sxs-lookup"><span data-stu-id="7b47d-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="7b47d-155">Funkce na straně klienta se nachází v `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` a `CreditCardTokenProvider` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="7b47d-156">Ve službě, se funkce nachází v `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` a `CreditCardTokenAuthorizationPolicy` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b47d-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```
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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="7b47d-157">Zobrazení informací o volajícím.</span><span class="sxs-lookup"><span data-stu-id="7b47d-157">Displaying the Callers' Information</span></span>
 <span data-ttu-id="7b47d-158">K zobrazení informací volajícího, použijte `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7b47d-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="7b47d-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizaci deklarací identity přidružené k aktuální volajícího.</span><span class="sxs-lookup"><span data-stu-id="7b47d-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="7b47d-160">Deklarace identity jsou poskytována `CreditCardToken` třídy v jeho `AuthorizationPolicies` kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b47d-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

```
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,
        Rights.PossessProperty);
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
                 return String.Format(
                   "Credit card '{0}' issued by '{1}'",
                   creditCardNumber, issuer);
        }
    }
    return "Credit card is not known";
}
```

 <span data-ttu-id="7b47d-161">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47d-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7b47d-162">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="7b47d-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="7b47d-163">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="7b47d-163">Setup Batch File</span></span>
 <span data-ttu-id="7b47d-164">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="7b47d-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="7b47d-165">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="7b47d-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="7b47d-166">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7b47d-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="7b47d-167">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="7b47d-167">Creating the server certificate:</span></span>

     <span data-ttu-id="7b47d-168">Následující řádky z `Setup.bat` dávkový soubor vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="7b47d-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="7b47d-169">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="7b47d-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7b47d-170">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="7b47d-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7b47d-171">V tomto souboru batch výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="7b47d-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="7b47d-172">Pokud změníte `%SERVER_NAME%` proměnné, musíte projít Client.cs a Service.cs soubory a nahraďte všechny výskyty místního hostitele s názvem serveru, který používáte v skript Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="7b47d-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="7b47d-173">Certifikát je uložen v úložišti (osobních) v části `LocalMachine` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b47d-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="7b47d-174">Certifikát je uložen v úložišti LocalMachine pro služby hostované v IIS.</span><span class="sxs-lookup"><span data-stu-id="7b47d-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="7b47d-175">V místním prostředí služby upravte dávkový soubor pro uložení certifikátu klienta v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7b47d-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="7b47d-176">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="7b47d-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="7b47d-177">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="7b47d-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7b47d-178">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47d-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7b47d-179">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7b47d-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="7b47d-180">Povolit přístup k privátnímu klíči certifikátu ze služby hostované v IIS, musíte uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělena příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="7b47d-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="7b47d-181">Toho lze dosáhnout poslední kroky v skript Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="7b47d-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
>  <span data-ttu-id="7b47d-182">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="7b47d-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="7b47d-183">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="7b47d-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7b47d-184">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="7b47d-184">To set up and build the sample</span></span>

1.  <span data-ttu-id="7b47d-185">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b47d-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="7b47d-186">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b47d-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7b47d-187">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="7b47d-187">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="7b47d-188">Otevřete okno příkazového řádku sady Visual Studio 2012 s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="7b47d-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="7b47d-189">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="7b47d-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
>  <span data-ttu-id="7b47d-190">Je potřeba certifikáty odebrat spuštěním Cleanup.bat po dokončení s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="7b47d-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="7b47d-191">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="7b47d-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="7b47d-192">Spusťte Client.exe z client\bin adresáře.</span><span class="sxs-lookup"><span data-stu-id="7b47d-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="7b47d-193">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="7b47d-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="7b47d-194">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7b47d-194">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="7b47d-195">Ke spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="7b47d-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="7b47d-196">Vytvoření adresáře na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="7b47d-197">Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="7b47d-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="7b47d-198">Nezapomeňte zkopírovat CreditCardFile.txt; v opačném případě authenticator platební karty nelze ověřit informace o platební kartě odeslaných z klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47d-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="7b47d-199">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="7b47d-200">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="7b47d-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7b47d-201">Můžete si ho pomocí Setup.bat změníte-li vytvořit `%SERVER_NAME%` proměnné pro plně kvalifikovaný název počítače, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="7b47d-202">Všimněte si, že se soubor Setup.bat musí být spuštěn v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="7b47d-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="7b47d-203">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47d-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="7b47d-204">Musíte to provést jenom v případě, že certifikát serveru není vystavený důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="7b47d-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="7b47d-205">V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu k zadání názvu počítače plně kvalifikovaný, místo localhost.</span><span class="sxs-lookup"><span data-stu-id="7b47d-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="7b47d-206">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="7b47d-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="7b47d-207">V souboru Client.cs změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="7b47d-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="7b47d-208">V souboru Client.cs změňte název subjektu certifikátu X.509 služby tak, aby odpovídala plně kvalifikovaný název vzdáleného hostitele, místo localhost.</span><span class="sxs-lookup"><span data-stu-id="7b47d-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="7b47d-209">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7b47d-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="7b47d-210">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7b47d-210">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7b47d-211">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="7b47d-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="7b47d-212">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="7b47d-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b47d-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b47d-213">See Also</span></span>
