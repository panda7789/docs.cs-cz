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
ms.openlocfilehash: 34d40cb9b0f4929330473ae0dc2f4c12dd309270
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840164"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Postupy: Připojení k webové službě pomocí Windows Forms BindingSource
Pokud chcete vytvořit vazbu ovládacího prvku Windows Form do výsledků získaných z volání webové služby XML, můžete použít <xref:System.Windows.Forms.BindingSource> komponenty. Tento postup je podobný vazby <xref:System.Windows.Forms.BindingSource> komponentu do typu. Je nutné vytvořit proxy server na straně klienta, který obsahuje metody a typy, které jsou vystavené webové služby. Generování proxy server na straně klienta z webové služby (.asmx) samotný nebo jeho soubor webové služby WSDL (Description Language). Váš proxy server na straně klienta navíc musí vystavit pole komplexní typy použité ve webové službě jako veřejné vlastnosti. Pak vytvoříte vazbu <xref:System.Windows.Forms.BindingSource> na jeden z typů v webové služby serveru proxy.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>K vytvoření a připojení k proxy serveru na straně klienta  
  
1.  Vytvoření formuláře Windows v adresáři podle vašeho výběru s odpovídající obor názvů.  
  
2.  Přidat <xref:System.Windows.Forms.BindingSource> komponentu do formuláře.  
  
3.  Otevřít [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] příkazový řádek a přejděte do stejného adresáře, umístěný ve formuláři.  
  
4.  Pomocí nástroje WSDL zadat `wsdl` a adresa URL pro .asmx nebo souboru WSDL pro webovou službu, za nímž následuje obor názvů vaší aplikace a volitelně jazyk k práci používáte.  
  
     Následující příklad kódu používá webovou službu v `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Například pro typ jazyka C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, nebo pro typ jazyka Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Předáním cesty do jazyka WSDL jako argument nástroj vygeneruje proxy server na straně klienta ve stejném adresáři a obor názvů jako vaši aplikaci v daném jazyce. Pokud používáte Visual Studio, přidejte soubor do projektu.  
  
5.  Vyberte typ proxy serveru na straně klienta k vytvoření vazby.  
  
     Obvykle se jedná o typ vrácený metodou nabízené webové služby. Pole zvolený typ musí být vystavené jako veřejné vlastnosti pro účely vazby.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Nastavte <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> na požadovaný typ, který je obsažen v proxy serveru webové služby na straně klienta.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>K vytvoření vazby ovládacích prvků do objektu BindingSource, který je vázán k webové službě  
  
-   Vytvoření vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>, veřejná vlastnost typ webové služby, který chcete, aby se předá jako parametr.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.BindingSource> součást webové služby a jak vytvořit vazbu textové pole <xref:System.Windows.Forms.BindingSource> komponenty. Když kliknete na tlačítko, je volána metoda webové služby a výsledky se zobrazí v `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Toto je úplný příklad, který zahrnuje `Main` metoda a zkrácenou verzi kódu proxy server na straně klienta.  
  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing, System.Web.Services, System.Windows.Forms a System.Xml.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
