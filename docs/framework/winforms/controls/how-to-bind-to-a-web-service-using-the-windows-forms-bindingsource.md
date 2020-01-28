---
title: Vytvoření vazby na webovou službu pomocí objektu BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746682"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Postupy: Připojení k webové službě pomocí Windows Forms BindingSource
Chcete-li navazovat ovládací prvek Windows Form na výsledky získané z volání webové služby XML, můžete použít komponentu <xref:System.Windows.Forms.BindingSource>. Tento postup je podobný jako vytvoření vazby <xref:System.Windows.Forms.BindingSource> komponenty na typ. Musíte vytvořit proxy server na straně klienta, který obsahuje metody a typy zveřejněné webovou službou. Vygenerujete proxy server na straně klienta z samotné webové služby (. asmx) nebo z jeho souboru WSDL (Web Services Description Language). Kromě toho musí proxy server na straně klienta zveřejnit pole komplexních typů, které webová služba používá jako veřejné vlastnosti. Potom svážete <xref:System.Windows.Forms.BindingSource> k jednomu z typů zveřejněných v proxy webové služby.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Vytvoření vazby na proxy server na straně klienta  
  
1. Vytvořte formulář Windows v adresáři dle vašeho výběru s odpovídajícím oborem názvů.  
  
2. Přidejte do formuláře komponentu <xref:System.Windows.Forms.BindingSource>.  
  
3. Otevřete příkazový řádek sady Windows Software Development Kit (SDK) a přejděte do stejného adresáře, ve kterém se nachází formulář.  
  
4. Pomocí nástroje WSDL zadejte `wsdl` a adresu URL pro soubor. asmx nebo WSDL pro webovou službu, za kterou následuje obor názvů vaší aplikace, a volitelně i jazyk, ve kterém pracujete.  
  
     Následující příklad kódu používá webovou službu, která se nachází na `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Například pro C# typ `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`nebo pro Visual Basic typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Předání cesty jako argumentu nástroje WSDL vygeneruje proxy na straně klienta ve stejném adresáři a oboru názvů jako vaše aplikace v zadaném jazyce. Pokud používáte aplikaci Visual Studio, přidejte soubor do projektu.  
  
5. Vyberte typ v proxy straně klienta, ke kterému se má vytvořit vazba.  
  
     Obvykle se jedná o typ vrácený metodou nabízenou webovou službou. Pole zvoleného typu musí být vystavena jako veřejné vlastnosti pro účely vazby.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. Nastavte vlastnost <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource> na požadovaný typ, který je obsažený v proxy straně klienta webové služby.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Vytvoření vazby ovládacích prvků k objektu BindingSource, který je svázán s webovou službou  
  
- Navažte ovládací prvky na <xref:System.Windows.Forms.BindingSource>a předejte veřejnou vlastnost typu webové služby, kterou chcete zadat jako parametr.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit navázání součásti <xref:System.Windows.Forms.BindingSource> k webové službě a jak navazovat textové pole na <xref:System.Windows.Forms.BindingSource> komponentu. Po kliknutí na tlačítko se zavolá metoda webové služby a výsledky se zobrazí v `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Toto je kompletní příklad, který obsahuje metodu `Main` a zkrácenou verzi kódu proxy na straně klienta.  
  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing, System. Web. Services, System. Windows. Forms a System. XML.  
  
## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
