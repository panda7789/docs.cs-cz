---
title: Přehled nespravovaných aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: 0b4c3e738848be1ead2adeb1945e168c9db60071
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732532"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms a přehled nespravovaných aplikací
Model Windows Forms aplikace a ovládací prvky mohou spolupracovat s nespravovanými aplikacemi, s některými upozorněními. V následujících částech najdete popis scénářů a konfigurací, které model Windows Forms aplikace a ovládací prvky podporují, a ty, které nepodporují.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>model Windows Forms ovládací prvky a aplikace ActiveX  
 S výjimkou aplikací Microsoft Internet Explorer a Microsoft Foundation Classes (MFC) nejsou ovládací prvky model Windows Forms podporovány v aplikacích navržených pro hostování ovládacích prvků ActiveX. Jiné aplikace a vývojové nástroje, které jsou schopné hostovat ovládací prvky ActiveX, včetně kontejnerů testů ActiveX z verzí sady Visual Studio, které jsou starší než Visual Studio .NET 2003, nejsou pro ovládací prvky model Windows Forms podporovány.  
  
 Tato omezení platí také pro použití model Windows Formsch ovládacích prvků prostřednictvím zprostředkovatele komunikace s objekty COM komponent modelu COM. Použití ovládacího prvku model Windows Forms přes obálku s podporou modelu COM (doleva) je podporováno pouze v aplikaci Internet Explorer. Další informace o zprostředkovateli komunikace s objekty COM naleznete v tématu.  
  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 V následující tabulce je uvedena dostupná podpora hostování ActiveX pro ovládací prvky model Windows Forms.  
  
|Verze model Windows Forms|Podpora|  
|---------------------------|-------------|  
|.NET Framework verze 1,0|Internet Explorer 5,01 a novější verze|  
|.NET Framework verze 1,1 a novější|Internet Explorer 5,01 a novější verze<br /><br /> Microsoft Foundation Classes (MFC) 7,0 a novější|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hostování komponent model Windows Forms jako ovládacích prvků ActiveX  
 V .NET Framework 1,1 byla podpora rozšířena tak, aby zahrnovala knihovnu MFC 7,0 a novější verze. Tato podpora zahrnuje libovolný kontejner, který je plně kompatibilní s kontejnerem ovládacích prvků ActiveX MFC 7,0 a novějším.  
  
 Nicméně registrace ovládacích prvků model Windows Forms jako ovládacích prvků ActiveX není podporována. Také volání metody `com.ms.win32.Ole32.CoCreateInstance` pro ovládací prvky model Windows Forms není podporováno. Podporovaná je jenom spravovaná aktivace model Windows Formsch ovládacích prvků. Po vytvoření ovládacího prvku model Windows Forms jej můžete hostovat v aplikaci knihovny MFC stejně jako s ovládacím prvkem ActiveX.  
  
 Chcete-li použít ovládací prvky model Windows Forms v nespravované aplikaci, je nutné buď hostovat modul CLR pomocí nespravovaného rozhraní API C++ pro hostování CLR, nebo použít funkce spolupráce. Doporučené řešení C++ je použití funkcí spolupráce.  
  
## <a name="windows-forms-in-com-client-applications"></a>model Windows Forms v klientských aplikacích modelu COM  
 Při otevření formuláře Windows z klientské aplikace modelu COM, jako je například aplikace Visual Basic 6,0 nebo aplikace MFC, se formulář může chovat neočekávaně. Například při stisknutí klávesy TAB se fokus nemění z jednoho ovládacího prvku na jiný ovládací prvek. Když stisknete klávesu ENTER, zatímco příkazové tlačítko má fokus, není vyvolána událost <xref:System.Windows.Forms.Control.Click> tlačítka. Můžete také zaznamenat neočekávané chování pro stisknutí kláves nebo aktivitu myši.  
  
 K tomuto chování dochází, protože nespravované aplikace neimplementuje podporu smyčky zpráv, kterou model Windows Forms vyžaduje, aby správně fungovala. Smyčka zprávy, kterou poskytuje klientská aplikace modelu COM, se od smyčky zpráv model Windows Forms liší.  
  
 Smyčka zpráv aplikace je interní smyčka programu, která načítá zprávy z fronty zpráv vlákna, překládá je a odesílá do aplikace, aby ji bylo možné zpracovat. Smyčka zpráv pro formulář Windows nemá stejnou architekturu jako smyčka zpráv, kterou používají dřívější aplikace, jako jsou například aplikace Visual Basic 6,0 a aplikace MFC. Zprávy oken, které jsou publikovány do smyčky zpráv, mohou být zpracovány odlišně, než systém Windows Form očekává. Proto může dojít k neočekávanému chování. Některé kombinace klávesových úhozů nemusí fungovat, některé aktivity myši nemusí fungovat nebo některé události nemusejí být vyvolány podle očekávání.  
  
## <a name="resolving-interoperability-issues"></a>Řešení problémů s interoperabilitou  
 Tyto problémy můžete vyřešit zobrazením formuláře ve smyčce zprávy .NET Framework, která je vytvořena pomocí metody <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>.  
  
 Chcete-li, aby formulář Windows pracoval správně z klientské aplikace modelu COM, je nutné jej spustit ve smyčce model Windows Forms zpráv. K tomu použijte jeden z následujících přístupů:  
  
- K zobrazení formuláře Windows použijte metodu <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md).  
  
- Zobrazí každý formulář Windows na novém vlákně. Další informace najdete v tématu [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Viz také:

- [Model Windows Forms a nespravované aplikace](windows-forms-and-unmanaged-applications.md)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Ukázky vzájemné funkční spolupráce modelu COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/cxcz83xf(v=vs.90))
- [Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)
- [Vystavení komponent architektury .NET Framework pro COM](../../interop/exposing-dotnet-components-to-com.md)
- [Zabalení sestavení pro model COM](../../interop/packaging-an-assembly-for-com.md)
- [Registrování sestav pomocí modelu COM](../../interop/registering-assemblies-with-com.md)
- [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
