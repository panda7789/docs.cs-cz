---
title: 'Postupy: Připojení k webové službě pomocí Windows Forms BindingSource'
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
ms.openlocfilehash: 5a5db651b0690aae393666124c8d33402d57a189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Postupy: Připojení k webové službě pomocí Windows Forms BindingSource
Pokud chcete vytvořit vazbu ovládacího prvku formuláře Windows do výsledků získaných z volání webové služby XML, můžete použít <xref:System.Windows.Forms.BindingSource> součásti. Tento postup je podobný vazby <xref:System.Windows.Forms.BindingSource> součásti typu. Je nutné vytvořit proxy server na straně klienta, který obsahuje metody a typy, které jsou vystavené webovou službu. Vygenerování proxy server na straně klienta z webové služby (.asmx) sám sebe nebo jeho webové služby (soubor Description Language WSDL). Váš klientský proxy server musí navíc vystavovat pole komplexní typy používané webovou službu jako veřejné vlastnosti. Pak vytvořte vazbu <xref:System.Windows.Forms.BindingSource> na jeden z typů, které jsou zveřejněné na webu služby proxy serveru.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Vytvoření a vytvořit vazbu na straně klienta proxy  
  
1.  Vytvoření formuláře Windows v adresáři podle vaší volby, s odpovídající obor názvů.  
  
2.  Přidat <xref:System.Windows.Forms.BindingSource> součásti pro formulář.  
  
3.  Otevřete [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] příkazový řádek a přejděte na stejný adresář, který svého formuláře se nachází v.  
  
4.  Pomocí nástroje WSDL zadejte `wsdl` adresu URL pro .asmx nebo soubor WSDL pro webovou službu, za nímž následuje obor názvů aplikace a volitelně jazyk, ve které pracujete.  
  
     Následující příklad kódu používá webovou službu v http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx. Například pro C# typ `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, nebo pro typ jazyka Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Předání cestu jako argument schématu WSDL nástroj vygeneruje proxy serveru klienta ve stejné adresáře a oboru názvů jako je aplikace, v daném jazyce. Pokud používáte Visual Studio, přidejte do projektu soubor.  
  
5.  Vyberte typ proxy serveru klienta pro vazbu.  
  
     To je obvykle typ vrácený metodou nabízené webovou službou. Pole zvoleného typu musí být zveřejněné jako veřejné vlastnosti pro účely vazby.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Nastavte <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> na typ, který chcete obsažené v proxy serveru webové služby klienta.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Vázání ovládacích prvků na BindingSource, který je vázaný k webové službě  
  
-   Vytvoření vazby ovládacích prvků na <xref:System.Windows.Forms.BindingSource>, předávání veřejná vlastnost typu webové služby, který chcete jako parametr.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.BindingSource> součást webové služby a jak vytvořit vazbu textové pole k <xref:System.Windows.Forms.BindingSource> součásti. Když kliknete na tlačítko, je volána metoda webové služby a výsledky se zobrazí v `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Toto je kompletní příklad, který zahrnuje `Main` metoda a zkrácená verze kódu proxy server na straně klienta.  
  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing, System.Web.Services, System.Windows.Forms a System.Xml sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
