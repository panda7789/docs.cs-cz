---
title: 'Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: caf0a071d65746f1027052e648ade538d62dc4bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic
Při vytváření nové aplikace nebo součásti, je nejlepší vytvořit sestavení rozhraní .NET Framework. Ale jazyka Visual Basic také umožňuje snadno vystavit rozhraní .NET Framework komponenty modelu COM. To umožňuje poskytovat nové součásti pro starší aplikace sady, které vyžadují COM – součásti. Tento návod ukazuje, jak používat Visual Basic vystavit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objekty jako objekty modelu COM, s i bez šablona třídy COM.  
  
 Nejjednodušší způsob, jak vystavit objektů COM je pomocí šablony třídy COM. Šablona třídy COM vytvoří novou třídu a pak nakonfiguruje projektu pro generování tříd a interoperabilita vrstvě jako objekt COM a zaregistrovat ho u operačního systému.  
  
> [!NOTE]
>  I když můžete také zveřejnit třídu vytvořit jako objekt COM pro nespravovaného kódu pro použití v jazyce Visual Basic, není objekt true COM a nemůže být použit jazyka Visual Basic. Další informace najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Chcete-li vytvořit objekt modelu COM pomocí šablony třídy COM  
  
1.  Otevřete nový projekt aplikace Windows z **soubor** nabídky kliknutím **nový projekt**.  
  
2.  V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána systému Windows. Vyberte **knihovny tříd** z **šablony** seznamu a pak klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3.  Vyberte **přidat novou položku** z **projektu** nabídky. **Přidat novou položku** se zobrazí dialogové okno.  
  
4.  Vyberte **třídy COM** z **šablony** seznamu a pak klikněte na tlačítko **přidat**. Visual Basic přidá novou třídu a nakonfiguruje nového projektu pro zprostředkovatele komunikace s objekty COM.  
  
5.  Přidejte kód například události, vlastnosti a metody pro třídu COM.  
  
6.  Vyberte **sestavení ClassLibrary1** z **sestavení** nabídky. Visual Basic sestavení sestavení a zaregistruje objekt COM s operačním systémem.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Vytváření objektů modelu COM bez šablony třídy COM  
 Můžete také vytvořit třídu COM ručně místo pomocí šablony třídy COM. Tento postup je užitečné, když pracujete z příkazového řádku, nebo pokud potřebujete větší kontrolu nad jak jsou definovány COM – objekty.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Nastavení projektu pro generování objektu COM  
  
1.  Otevřete nový projekt aplikace Windows z **soubor** nabídky kliknutím **NewProject**.  
  
2.  V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána systému Windows. Vyberte **knihovny tříd** z **šablony** seznamu a pak klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti**. **Návrhář projektu** se zobrazí.  
  
4.  Klikněte **zkompilovat** kartě.  
  
5.  Vyberte **zaregistrovat zprostředkovatel komunikace s objekty COM** zaškrtávací políčko.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Nastavit kód ve třídě vytvoříte objekt modelu COM  
  
1.  V **Průzkumníku řešení**, dvakrát klikněte na **Class1.vb** k zobrazení jeho kódu.  
  
2.  Přejmenujte třídy pro `ComClass1`.  
  
3.  Přidejte následující konstanty pro `ComClass1`. Se uloží konstanty globálně jedinečný identifikátor (GUID), které je potřeba mít objektů COM.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Na **nástroje** nabídky, klikněte na tlačítko **vytvořit Guid**. V **vytvořit GUID** dialogové okno, klikněte na tlačítko **registru formátu** a pak klikněte na **kopie**. Klikněte na tlačítko **ukončení**.  
  
5.  Nahraďte prázdný řetězec pro `ClassId` s identifikátorem GUID, složené závorky odebrání úvodní a koncové. Například, pokud identifikátor GUID poskytované Guidgen – je `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` pak váš kód by měl vypadat takto.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Opakujte předchozí kroky pro `InterfaceId` a `EventsId` konstanty, jako v následujícím příkladu.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Ujistěte se, že jsou identifikátory GUID nových a jedinečných; příslušné součásti COM, jinak hodnota mohla být v konfliktu s ostatními součástmi COM.  
  
7.  Přidat `ComClass` atribut `ComClass1`, určení identifikátory GUID pro ID třídy, rozhraní ID a ID událostí jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Třídy COM musí mít bez parametrů `Public Sub New()` konstruktoru nebo třídě se neregistruje správně. Přidejte do třídy konstruktor bez parametrů:  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Přidejte do třídy, koncová její vlastnosti, metod a události `End Class` příkaz. Vyberte **sestavit řešení** z **sestavení** nabídky. Visual Basic sestavení sestavení a zaregistruje objekt COM s operačním systémem.  
  
    > [!NOTE]
    >  Objekty COM, které můžete vygenerovat pomocí jazyka Visual Basic nelze použít jiné aplikace Visual Basic, protože nejsou true COM – objekty. Pokusy o přidání odkazů na tyto objekty COM vyvolá chybu. Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
