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
ms.openlocfilehash: 1f7cfa17ce763ff84eeb052a4ea1a3a900970782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows Forms a přehled nespravovaných aplikací
Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravovaných aplikací se některých aspektů. Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows Forms – ovládací prvky a aplikací ActiveX  
 S výjimkou aplikace Microsoft Internet Explorer a Microsoft Foundation třídy (MFC) nejsou podporovány Windows Forms – ovládací prvky v aplikacích, které jsou navržené tak, aby hostitelské ovládací prvky ActiveX. Ostatní aplikace a nástroje pro vývoj, které podporují hostování ovládacích prvků ActiveX, včetně testovacích kontejnerů ActiveX z verzí sady Visual Studio, které jsou starší než Visual Studio .NET 2003, nejsou podporované hostitelé pro ovládací prvky Windows Forms.  
  
 Tato omezení platí také pro používání ovládacích prvků Windows Forms pomocí zprostředkovatele komunikace s objekty Component Object Model COM. Použití ovládacího prvku Windows Forms pomocí obálka volatelná aplikacemi COM (doleva) je podporováno pouze v aplikaci Internet Explorer. Další informace o zprostředkovatel komunikace s objekty COM najdete v tématu  
  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 V následující tabulce jsou k dispozici ActiveX hostování podpora pro ovládací prvky Windows Forms.  
  
|Verze Windows Forms|Podpora|  
|---------------------------|-------------|  
|Rozhraní .NET framework verze 1.0|Internet Explorer 5.01 a novější verze|  
|Rozhraní .NET framework verze 1.1 nebo novější|Internet Explorer 5.01 a novější verze<br /><br /> Microsoft Foundation třídy (MFC) 7.0 nebo novější|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hostování součásti Windows Forms jako ovládací prvky ActiveX  
 V rozhraní .NET Framework 1.1 byla rozšířené podpory MFC 7.0 a novější verze. Tato podpora zahrnuje všechny kontejner, který je plně kompatibilní se MFC 7.0 a pozdější kontejneru ovládacího prvku ActiveX.  
  
 Registrace ovládacích prvků Windows Forms jako ovládací prvky ActiveX však není podporován. Navíc volání `com.ms.win32.Ole32.CoCreateInstance` metoda pro Windows Forms – ovládací prvky není podporována. Je podporován pouze spravované aktivace ovládacích prvků Windows Forms. Po vytvoření ovládacího prvku Windows Forms, můžete ji hostovat v aplikaci MFC stejně jako u ovládacího prvku ActiveX.  
  
 Pokud chcete použít ovládací prvky Windows Forms v nespravované aplikaci, musíte buď hostování CLR pomocí nespravované CLR hostování rozhraní API nebo používat funkce interoperability C++. Pomocí funkcí interoperability C++ je doporučená řešení.  
  
## <a name="windows-forms-in-com-client-applications"></a>Windows Forms v klientské aplikace modelu COM  
 Při otevření formuláře Windows z klientské aplikace modelu COM, jako je například aplikace Visual Basic 6.0 nebo aplikace MFC formuláře může neočekávanému chování. Například po stisknutí klávesy TAB, pak se fokus nezmění z jednoho ovládacího prvku na další ovládací prvek. Když se při příkazového tlačítka má právě fokus, tlačítko na stiskněte klávesu ENTER <xref:System.Windows.Forms.Control.Click> událost není aktivována. Může také dochází k neočekávanému chování pro stisknutí kláves nebo myš aktivity.  
  
 K tomuto chování dochází, protože nespravovaná aplikace neimplementuje podporu zpráva smyčky, kterou Windows Forms vyžaduje, aby správně fungovat. Zpráva smyčky poskytované klientská aplikace modelu COM se zásadně liší od smyčce zpráv Windows Forms.  
  
 Aplikace zpráva, že smyčka je smyčky interního programu, která načítá zprávy z fronty zpráv vlákno, znamená, že je a poté je odešle do aplikace zpracovávat. Zpráva smyčky pro formuláře Windows nemá stejnou architekturu jako smyčky zpráv, které poskytují starší aplikace, jako je aplikace Visual Basic 6.0 a aplikace MFC. Okno zprávy, které jsou odeslány na smyčce zpráv může zpracovány jinak, než se očekává formuláře Windows. Proto může dojít k neočekávanému chování. Některé kombinací kláves nemusí fungovat, nemusí fungovat nějakou aktivitu myši nebo některé události nemusí být vyvolány podle očekávání.  
  
## <a name="resolving-interoperability-issues"></a>Řešení potíží s interoperabilitou  
 Tyto problémy můžete vyřešit tím, že zobrazuje formuláře na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, která je vytvořena pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.  
  
 Chcete-li pracovní formuláře Windows správně z klientské aplikace modelu COM, je nutné jej spustit ve smyčce zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows. Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Zobrazení jednotlivých formulářů Windows na nové vlákno. Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Viz také  
 [Model Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Interoperabilita modelů COM v aplikacích .NET Framework](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Ukázky vzájemná funkční spolupráce COM](http://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [Vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Zabalení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrování sestav pomocí modelu COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
