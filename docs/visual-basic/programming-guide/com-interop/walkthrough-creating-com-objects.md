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
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245684"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic
Při vytváření nové aplikace nebo komponenty, je nejlepší vytvořit sestavení rozhraní .NET Framework. Ale jazyka Visual Basic také umožňuje snadno vystavit součásti rozhraní .NET Framework do modelu COM. To umožňuje poskytovat nové součásti pro starší aplikace sad, které vyžadují komponenty modelu COM. Tento návod ukazuje, jak pomocí jazyka Visual Basic k vystavení [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objekty jako objekty modelu COM, s i bez šablony třídy modelu COM.  
  
 Nejjednodušší způsob, jak vystavit objekty modelu COM je pomocí šablony třídy modelu COM. Šablona třídy modelu COM vytvoří novou třídu a pak nakonfiguruje projekt na vrstvě třídy a vzájemná funkční spolupráce jako objekt modelu COM vygeneruje a zaregistruje ho s operačním systémem.  
  
> [!NOTE]
>  I když můžete také zpřístupní třídu vytvořené v jazyce Visual Basic jako objekt modelu COM pro nespravovaný kód, který použijete, není objekt modelu COM true a nelze použít v jazyce Visual Basic. Další informace najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Chcete-li vytvořit objekt modelu COM s použitím šablony třídy modelu COM  
  
1.  Otevřete nový projekt aplikace Windows z **souboru** nabídky kliknutím **nový projekt**.  
  
2.  V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána Windows. Vyberte **knihovny tříd** z **šablony** seznamu a potom klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3.  Vyberte **přidat novou položku** z **projektu** nabídky. **Přidat novou položku** se zobrazí dialogové okno.  
  
4.  Vyberte **třídy COM** z **šablony** seznamu a potom klikněte na tlačítko **přidat**. Visual Basic přidá novou třídu a nakonfiguruje nový projekt pro spolupráci s COM.  
  
5.  Přidání kódu, jako jsou vlastnosti, metody a události do třídy modelu COM.  
  
6.  Vyberte **sestavení ClassLibrary1** z **sestavení** nabídky. Visual Basic vytvoří sestavení a registruje objekt modelu COM s operačním systémem.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Vytváření objektů COM bez šablony třídy modelu COM  
 Můžete také vytvořit třídu COM ručně místo pomocí šablony třídy modelu COM. Tento postup je užitečný při práci z příkazového řádku, nebo pokud potřebujete větší kontrolu nad jak objekty modelu COM jsou definovány.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Nastavení projektu pro generování objekt modelu COM  
  
1.  Otevřete nový projekt aplikace Windows z **souboru** nabídky kliknutím **NewProject**.  
  
2.  V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána Windows. Vyberte **knihovny tříd** z **šablony** seznamu a potom klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**. **Návrháře projektu** se zobrazí.  
  
4.  Klikněte na tlačítko **kompilaci** kartu.  
  
5.  Vyberte **zaregistrovat pro interoperabilitu COM** zaškrtávací políčko.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>K nastavení kódu ve své třídě pro vytvoření objektu modelu COM  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Class1.vb** zobrazíte jeho kód.  
  
2.  Přejmenujte třídu na `ComClass1`.  
  
3.  Přidejte následující konstanty na `ComClass1`. Ukládají se konstanty globálně jedinečný identifikátor (GUID), které jsou objekty COM musí mít.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**. V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**. Klikněte na tlačítko **ukončovací**.  
  
5.  Prázdný řetězec pro nahrazení `ClassId` s identifikátorem GUID, odebírá se úvodní a koncové závorek. Například, pokud identifikátor GUID poskytl Guidgen – je `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` a váš kód by měl vypadat následovně.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Opakujte předchozí kroky pro `InterfaceId` a `EventsId` konstant, jako v následujícím příkladu.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Ujistěte se, že jsou identifikátory GUID nových a jedinečných; jinak vaše komponenty modelu COM může jsou v konfliktu s dalšími komponentami COM.  
  
7.  Přidat `ComClass` atribut `ComClass1`, zadejte identifikátory GUID pro ID třídy, rozhraní ID a události ID jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Třídy COM musí mít bez parametrů `Public Sub New()` konstruktor nebo třídy nebude správně zaregistrována. Přidejte konstruktor pro třídu:  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Přidejte do třídy, koncové ji vlastnosti, metody a události `End Class` příkazu. Vyberte **sestavit řešení** z **sestavení** nabídky. Visual Basic vytvoří sestavení a registruje objekt modelu COM s operačním systémem.  
  
    > [!NOTE]
    >  Objekty COM, které vygenerujete pomocí jazyka Visual Basic nelze použít jiné aplikace Visual Basic, protože nejsou splněny objektů COM. Pokusy o přidání odkazů na tyto objekty modelu COM vyvolá chybu. Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
