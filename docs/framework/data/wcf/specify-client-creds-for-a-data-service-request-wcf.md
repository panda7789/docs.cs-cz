---
title: 'Postupy: Zadejte přihlašovací údaje klienta datové služby žádosti (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: ca2ed1fcf113e06535c8900e5836eb64f9b23958
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518133"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Postupy: Zadejte přihlašovací údaje klienta datové služby žádosti (WCF Data Services)
Ve výchozím nastavení, klientské knihovny neposkytuje přihlašovací údaje při odesílání požadavku do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Však můžete určit, že přihlašovací údaje se odešlou k ověření požadavků ve službě data zadáním <xref:System.Net.NetworkCredential> pro <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). V příkladu v tomto tématu ukazuje, jak explicitně zadat přihlašovací údaje, které jsou používány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta při vyžádání dat z datové služby.  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Můžete také použít [ukázková datová služba Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) , který je publikovaný na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webové stránky; Tato ukázková data service je jen pro čtení a pokusu o uložení změny vrátí chybu. Ukázková data services – na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webovou stránku Povolit anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je na stránce použití modelu code-behind pro Extensible Application Markup Language (XAML) soubor, který je hlavní stránky aplikace Windows Presentation Framework. Tento příklad zobrazuje `LoginWindow` instance shromažďovat ověřování přihlašovacích údajů od uživatele a pak pomocí těchto přihlašovacích údajů při požadavku na datovou službu.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Příklad  
 Následující XAML definuje hlavní stránky aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je na stránce použití modelu code-behind okna, která se používá ke shromažďování ověřovacích údajů od uživatele před provedením požadavku datové služby.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Příklad  
 Následující XAML definuje přihlášení aplikaci WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V příkladu v tomto tématu platí následující aspekty zabezpečení:  
  
-   Pokud chcete ověřit, že pověření uvedená v této ukázce fungovat, datová služba Northwind musí používat schéma ověřování než anonymní přístup. Web, který hostuje službu dat v opačném případě nebude požádat o přihlašovací údaje.  
  
-   Přihlašovací údaje uživatele by měly být vyžádány pouze během provádění a by neměl být uložené v mezipaměti. Přihlašovací údaje musí být uložen vždy bezpečné.  
  
-   Data odesílaná s Basic a ověřování algoritmem Digest se nešifrují, takže data můžete vidět nežádoucí osoba. Kromě toho pověření základního ověřování (uživatelské jméno a heslo) je odesíláno jako nezašifrovaný text a mohou být zachyceny.  
  
 Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení datových služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
