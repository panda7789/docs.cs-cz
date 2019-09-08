---
title: 'Postupy: Zadání přihlašovacích údajů klienta pro žádost o datovou službu (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: 4177b7f5138bd3e3ddd63e4a0d8d4bcb2be01fbb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790320"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Postupy: Zadání přihlašovacích údajů klienta pro žádost o datovou službu (WCF Data Services)
Ve výchozím nastavení neposkytuje Klientská knihovna při odesílání žádosti [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] službě pověření. Můžete ale zadat, aby se přihlašovací údaje poslaly k ověření požadavků na datovou službu, a to <xref:System.Net.NetworkCredential> zadáním <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnosti <xref:System.Data.Services.Client.DataServiceContext>pro. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md). V příkladu v tomto tématu se dozvíte, jak explicitně zadat přihlašovací údaje, které [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klient používá při požadování dat z datové služby.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md). Můžete také použít [ukázkovou datovou službu Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) publikovanou na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu. Tato ukázková datová služba je jen pro čtení a pokus o uložení změn vrátí chybu. Vzorové datové služby na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu umožňují anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí pro soubor jazyk Extensible Application Markup Language (XAML) (XAML), který je hlavní stránkou aplikace Windows Presentation Framework. V tomto příkladu se `LoginWindow` zobrazí instance pro shromažďování ověřovacích přihlašovacích údajů od uživatele a pak tyto přihlašovací údaje použije při vytváření žádosti o datovou službu.  
  
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
