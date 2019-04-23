---
title: Windows Forms a přehled nespravovaných aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: 63631378911a9ba95713e68fb19d8d08176c7562
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195641"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms a přehled nespravovaných aplikací
Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravované aplikace, se některé upozornění. Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Forms, ovládací prvky a aplikací ActiveX  
 S výjimkou Microsoft Internet Explorer a Microsoft Foundation Classes (MFC) nejsou podporovány ovládacích prvků Windows Forms v aplikacích, které jsou navržené tak, aby hostitelské ovládací prvky ActiveX. Ostatní aplikace a nástroje pro vývoj, které podporují hostování ovládacích prvků ActiveX, včetně testovacích kontejnerech ActiveX z verze sady Visual Studio, které jsou starší než Visual Studio .NET 2003, nejsou podporované hostitele pro ovládací prvky Windows Forms.  
  
 Tato omezení platí také pro použití ovládacích prvků Windows Forms pomocí zprostředkovatele komunikace s objekty Component Object Model COM. Použití ovládacího prvku Windows Forms prostřednictvím obálka volatelná aplikacemi COM (CCW) je podporováno pouze v aplikaci Internet Explorer. Další informace o spolupráci s COM naleznete v tématu  
  
 [Komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 V následující tabulce jsou uvedeny dostupné ActiveX hostování podpora pro ovládací prvky Windows Forms.  
  
|Verze Windows Forms|Podpora|  
|---------------------------|-------------|  
|Rozhraní .NET framework verze 1.0|Internet Explorer 5.01 a novější verze|  
|Rozhraní .NET framework verze 1.1 nebo novější|Internet Explorer 5.01 a novější verze<br /><br /> Microsoft Foundation Classes (MFC) 7.0 nebo novější|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hostování součásti Windows Forms jako ovládací prvky ActiveX  
 V rozhraní .NET Framework 1.1 se rozšířilo podporu knihovny MFC 7.0 a novější verze. Tato podpora zahrnuje jakýkoli kontejner, který je plně kompatibilní s MFC 7.0 a novější kontejneru ovládacího prvku ActiveX.  
  
 Registrace ovládacích prvků Windows Forms jako ovládací prvky ActiveX, ale není podporován. Také, volání `com.ms.win32.Ole32.CoCreateInstance` nepodporuje metodu pro ovládací prvky Windows Forms. Je podporován pouze spravované aktivace ovládacích prvků Windows Forms. Po vytvoření ovládacího prvku Windows Forms, můžete ho hostovat v aplikacích MFC stejně jako u ovládacího prvku ActiveX.  
  
 Použití ovládacích prvků Windows Forms v nespravované aplikaci, musíte buď hostování CLR pomocí nespravovaného rozhraní API pro hostování CLR nebo pomocí funkcí interoperability C++. Pomocí funkcí interoperability C++ je doporučené řešení.  
  
## <a name="windows-forms-in-com-client-applications"></a>Windows Forms v klientské aplikace modelu COM  
 Když otevřete formulář Windows z klientské aplikace modelu COM, jako je například aplikace v jazyce Visual Basic 6.0 nebo aplikace knihovny MFC může formuláři neočekávané chování. Například když stisknete klávesu TAB, zaměřuje nezmění z jednoho ovládacího prvku k jinému ovládacímu prvku. Když stisknutím klávesy ENTER při příkazové tlačítko má fokus, na tlačítko pro <xref:System.Windows.Forms.Control.Click> není vyvolána událost. Může také nastat, neočekávané chování úhozy na klávesnici nebo myš aktivity.  
  
 K tomuto chování dochází, protože nespravovaná aplikace neimplementuje podporu smyčky zpráv vyžadující fungování formulářů Windows. Smyčky zpráv poskytuje klientské aplikace modelu COM je zásadně liší od smyčky zpráv Windows Forms.  
  
 Aplikace zprávu, že je smyčka do interního programu smyčky, která načítá zprávy z fronty zpráv vlákna, přeloží je a potom je odešle do aplikace ke zpracování. Smyčky zpráv pro formulář Windows nemá stejnou architekturu jako smyčky zpráv, které poskytují starší aplikace, jako je aplikace Visual Basic 6.0 a aplikace knihovny MFC. Okno zpráv, které jsou odeslány do smyčky zpráv může zpracovány jinak, než se očekává, že formulář Windows. Proto může dojít k neočekávanému chování. Některé kombinací kláves nemusí fungovat, nemusí fungovat některé aktivity myši nebo některé události nemusí být vyvolány podle očekávání.  
  
## <a name="resolving-interoperability-issues"></a>Řešení potíží s interoperabilitou  
 Lze tyto problémy vyřešit zobrazení ve formuláři [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] smyčky zpráv, která je vytvořena pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.  
  
 Chcete-li pracovní formulář Windows správně z klientské aplikace modelu COM, musíte ho spustit na smyčku zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows. Další informace najdete v tématu [jak: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Každý formulář Windows pro zobrazení v novém vláknu. Další informace najdete v tématu [jak: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Viz také:

- [Model Windows Forms a nespravované aplikace](windows-forms-and-unmanaged-applications.md)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Ukázky vzájemná funkční spolupráce modelu COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/cxcz83xf(v=vs.90))
- [Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)
- [Vystavení komponent architektury .NET Framework pro COM](../../interop/exposing-dotnet-components-to-com.md)
- [Zabalení sestavení pro model COM](../../interop/packaging-an-assembly-for-com.md)
- [Registrování sestav pomocí modelu COM](../../interop/registering-assemblies-with-com.md)
- [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
