---
title: 'Postupy: zadání přihlašovacích údajů klienta pro žádost o datovou službu (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: bb25319e3a4b1f8c7a3586c546ce1d589b48e438
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975155"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Postupy: zadání přihlašovacích údajů klienta pro žádost o datovou službu (WCF Data Services)
Ve výchozím nastavení neposkytuje Klientská knihovna při odesílání požadavku službě OData přihlašovací údaje. Můžete ale zadat, aby se přihlašovací údaje poslaly k ověření požadavků na datovou službu, a to zadáním <xref:System.Net.NetworkCredential> pro vlastnost <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md). V příkladu v tomto tématu se dozvíte, jak explicitně zadat přihlašovací údaje, které používá klient [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] při požadování dat z datové služby.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md). Můžete také použít [ukázkovou datovou službu Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) , která je publikována na webu OData. Tato ukázková datová služba je jen pro čtení a při pokusu o uložení změn se vrátí chyba. Služba ukázkových dat na webu OData povoluje anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí pro soubor jazyk Extensible Application Markup Language (XAML) (XAML), který je hlavní stránkou aplikace Windows Presentation Framework. Tento příklad zobrazí instanci `LoginWindow` ke shromáždění přihlašovacích údajů od uživatele a pak použije tyto přihlašovací údaje při vytváření žádosti o datovou službu.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje hlavní stránku aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí okna, které se používá ke shromáždění přihlašovacích údajů od uživatele před odesláním požadavku na datovou službu.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje přihlášení aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 V příkladu v tomto tématu se vztahují následující požadavky na zabezpečení:  
  
- Chcete-li ověřit, zda přihlašovací údaje zadané v této ukázkové práci pracují, musí datová služba Northwind používat jiné schéma ověřování než anonymní přístup. V opačném případě web hostující datovou službu nebude požadovat přihlašovací údaje.  
  
- Přihlašovací údaje uživatele by se měly požadovat jenom během provádění a neměly by se ukládat do mezipaměti. Přihlašovací údaje se musí vždycky ukládat bezpečně.  
  
- Data odesílaná pomocí základního ověřování a ověřování algoritmem Digest nejsou šifrována, takže je lze zobrazit pomocí nežádoucí osoba. Přihlašovací údaje základního ověřování (uživatelské jméno a heslo) jsou navíc odesílány v nešifrovaném textu a lze je zachytit.  
  
 Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení datových služeb WCF Data Services](securing-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
