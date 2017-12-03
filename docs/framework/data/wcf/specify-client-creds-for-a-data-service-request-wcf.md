---
title: "Postupy: Zadejte pověření klienta pro žádosti o službu Data (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ee3fb9547ff0a4e949d9e3a7b251cdbc01d6001
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Postupy: Zadejte pověření klienta pro žádosti o službu Data (služby WCF Data Services)
Ve výchozím nastavení, klientské knihovny neposkytuje pověření při odesílání požadavku do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Ale můžete zadat, že přihlašovací údaje k ověřování žádostí službu data zadáním odeslány <xref:System.Net.NetworkCredential> pro <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). Příklad v tomto tématu ukazuje, jak explicitně zadat přihlašovací údaje, které jsou používány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta, když požadavek na data z datové služby.  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Můžete také [Northwind ukázková data služby](http://go.microsoft.com/fwlink/?LinkId=187426) , je publikována na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu; Tato ukázková data služby je jen pro čtení a pokus o uložení změn vrátí chybu. Ukázková data služby na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu povolit anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je z kódu stránky soubor rozšiřitelné aplikace Markup Language (XAML), který je na hlavní stránku aplikace Windows Presentation Framework. Tento příklad zobrazí `LoginWindow` instance ke shromažďování ověřování přihlašovacích údajů od uživatele a potom pomocí těchto přihlašovacích údajů při vytváření požadavku na službu data.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Příklad  
 Následující XAML definuje hlavní stránce aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je z kódu stránky pro okně, které se používá ke shromažďování ověřovací pověření od uživatele před prováděním žádost o službu data.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Příklad  
 Následující XAML definuje přihlášení aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V příkladu v tomto tématu platí následující aspekty zabezpečení:  
  
-   Pokud chcete ověřit, že pověření zadaná v této ukázce fungovat, musí používat službu data Northwind schéma ověřování než anonymní přístup. Webu, který hostuje službu data, jinak nebude vyžadovat přihlašovací údaje.  
  
-   Přihlašovací údaje uživatele byste měli požadovat jenom během provádění a nesmí být uložené v mezipaměti. Přihlašovací údaje musí být uložen vždy bezpečně.  
  
-   Data odeslaná s Basic a ověřování algoritmem Digest nejsou šifrována, takže nežádoucí osoba může zobrazit data. Kromě toho základní ověřovací pověření (uživatelské jméno a heslo) je odesíláno jako nezašifrovaný text a mohou být zachyceny.  
  
 Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení součásti WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
