---
title: 'Návod: Vytváření objektů COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 6ff23f73af384a1440bcebd4b6bac21714e01756
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051477"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic
Při vytváření nových aplikací nebo součástí je nejvhodnější vytvořit .NET Framework sestavení. Visual Basic ale také usnadňuje vystavení .NET Framework součásti modelu COM. To vám umožní poskytnout nové komponenty pro starší sady aplikací, které vyžadují komponenty modelu COM. Tento návod ukazuje, jak použít Visual Basic k vystavení objektů .NET Framework jako objektů COM, a to s šablonou třídy modelu COM i bez ní.  
  
 Nejjednodušší způsob, jak vystavit objekty COM, je použití šablony třídy modelu COM. Tato šablona vytvoří novou třídu a potom nakonfiguruje projekt tak, aby generoval třídu s vrstvou interoperability jako objekt modelu COM a zaregistroval ji v operačním systému.  
  
> [!NOTE]
> I když můžete vystavit třídu vytvořenou v Visual Basic jako objekt modelu COM pro použití nespravovaného kódu, nejedná se o skutečný objekt COM a nelze jej použít Visual Basic. Další informace najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Vytvoření objektu COM pomocí šablony třídy modelu COM  
  
1. Kliknutím na **Nový projekt**otevřete v nabídce **soubor** nový projekt aplikace pro Windows.  
  
2. V dialogovém okně **Nový projekt** v poli **typy projektů** zaškrtněte políčko Windows je vybráno. V seznamu **šablony** vyberte možnost **Knihovna tříd** a pak klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3. V nabídce **projekt** vyberte **Přidat novou položku** . Zobrazí se dialogové okno **Přidat novou položku**.  
  
4. V seznamu **šablony** vyberte možnost **třída com** a potom klikněte na tlačítko **Přidat**. Visual Basic přidá novou třídu a nakonfiguruje nový projekt pro zprostředkovatele komunikace s objekty COM.  
  
5. Přidejte do třídy COM kód, jako jsou vlastnosti, metody a události.  
  
6. V nabídce **sestavení** vyberte **Build ClassLibrary1** . Visual Basic sestavení sestavení a registruje objekt COM s operačním systémem.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Vytváření objektů COM bez šablony třídy modelu COM  
 Třídu COM lze také vytvořit ručně namísto použití šablony třídy modelu COM. Tento postup je užitečný při práci z příkazového řádku nebo v případě, že chcete mít větší kontrolu nad tím, jak jsou objekty modelu COM definovány.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Nastavení projektu pro vygenerování objektu COM  
  
1. Kliknutím na **NewProject**otevřete v nabídce **soubor** nový projekt aplikace pro Windows.  
  
2. V dialogovém okně **Nový projekt** v poli **typy projektů** zaškrtněte políčko Windows je vybráno. V seznamu **šablony** vyberte možnost **Knihovna tříd** a pak klikněte na tlačítko **OK**. Zobrazí se nový projekt.  
  
3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**. Zobrazí se **Návrhář projektu** .  
  
4. Klikněte na kartu **kompilovat** .  
  
5. Zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Nastavení kódu ve vaší třídě pro vytvoření objektu COM  
  
1. V **Průzkumník řešení**dvakrát klikněte na **Class1. vb** pro zobrazení kódu.  
  
2. Přejmenujte třídu na `ComClass1` .  
  
3. Přidejte následující konstanty do `ComClass1` . Budou ukládat konstanty globálně jedinečného identifikátoru (GUID), které objekty COM musí mít.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. V nabídce **nástroje** klikněte na příkaz **vytvořit identifikátor GUID**. V dialogovém okně **vytvořit GUID** klikněte na **Formát registru** a pak klikněte na **Kopírovat**. Klikněte na tlačítko **konec**.  
  
5. Nahraďte prázdný řetězec pro `ClassId` identifikátor GUID odebráním počátečních a koncových složených závorek. Například pokud je identifikátor GUID poskytovaný nástrojem Guidgen, `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` váš kód by měl vypadat takto.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Opakujte předchozí kroky pro `InterfaceId` `EventsId` konstanty a, jak je uvedeno v následujícím příkladu.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > Ujistěte se, že identifikátory GUID jsou nové a jedinečné; v opačném případě by komponenta modelu COM mohla být v konfliktu s jinými komponentami modelu COM.  
  
7. Přidejte `ComClass` atribut do `ComClass1` , zadejte identifikátory GUID pro ID třídy, ID rozhraní a ID událostí, jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. Třídy COM musí mít konstruktor bez parametrů `Public Sub New()` , jinak se třída nebude registrovat správně. Přidejte do třídy konstruktor bez parametrů:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Přidat vlastnosti, metody a události do třídy a ukončit ji `End Class` příkazem. V nabídce **sestavení** vyberte **sestavení řešení** . Visual Basic sestavení sestavení a registruje objekt COM s operačním systémem.  
  
    > [!NOTE]
    > Objekty modelu COM, které vygenerujete pomocí Visual Basic, nemohou být používány jinými Visual Basic aplikacemi, protože neplatí pro objekty COM. Pokusí se přidat odkazy na takové objekty COM a vyvolá chybu. Podrobnosti najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [Zprostředkovatel komunikace s objekty COM](index.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region direktiva](../../language-reference/directives/region-directive.md)
- [Interoperabilita modelů COM v aplikacích .NET Framework](com-interoperability-in-net-framework-applications.md)
- [Řešení potíží s interoperabilitou](troubleshooting-interoperability.md)
