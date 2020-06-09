---
title: 'Postupy: Zabezpečení služby certifikátem X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 10d6db63368ee55040f85f922b9483982e8ff264
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596965"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Postupy: Zabezpečení služby certifikátem X.509
Zabezpečení služby pomocí certifikátu X. 509 je základní technika, kterou používá většina vazeb ve službě Windows Communication Foundation (WCF). Toto téma vás provede jednotlivými kroky konfigurace samoobslužné služby s certifikátem X. 509.  
  
 Požadavek je platný certifikát, který lze použít k ověření serveru. Certifikát musí být vydán pro server důvěryhodnou certifikační autoritou. Není-li certifikát platný, nebude služba při pokusu o používání služby pro službu důvěřovat, a proto nebude provedeno žádné připojení. Další informace o používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Konfigurace služby s certifikátem pomocí kódu  
  
1. Vytvořte kontrakt služby a implementovanou službu. Další informace najdete v tématu [navrhování a implementace služeb](../designing-and-implementing-services.md).  
  
2. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message> , jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. Vytvořte dvě <xref:System.Type> proměnné, jednu pro typ kontraktu a implementovaný kontrakt, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. Vytvořte instanci <xref:System.Uri> třídy pro základní adresu služby. Vzhledem k tomu `WSHttpBinding` , že používá přenos pomocí protokolu HTTP, musí identifikátor URI (Uniform Resource Identifier) začínat tímto schématem nebo Windows Communication Foundation (WCF) vyvolá výjimku při otevření služby.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. Vytvořte novou instanci <xref:System.ServiceModel.ServiceHost> třídy s implementací proměnné typu kontraktu a identifikátor URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. Přidejte <xref:System.ServiceModel.Description.ServiceEndpoint> ke službě službu pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Předání kontraktu, vazby a adresy koncového bodu konstruktoru, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. Nepovinný parametr. Chcete-li načíst metadata ze služby, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objekt a nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na hodnotu `true` .  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy přidejte platný certifikát do služby. Metoda může použít jednu z několika metod k vyhledání certifikátu. V tomto příkladu se používá <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> výčet. Výčet Určuje, že poskytnutá hodnota je název entity, pro kterou byl certifikát vydán.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metody zahajte naslouchání služby. Pokud vytváříte konzolovou aplikaci, zavolejte <xref:System.Console.ReadLine%2A> metodu pro zachování služby ve stavu naslouchání.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu ke konfiguraci služby s certifikátem X. 509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro zkompilování kódu jsou vyžadovány následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
