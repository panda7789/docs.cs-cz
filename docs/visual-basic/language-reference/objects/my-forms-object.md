---
title: My.Forms – objekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350363"
---
# <a name="myforms-object"></a>My.Forms – objekt

Provides properties for accessing an instance of each Windows form declared in the current project.

## <a name="remarks"></a>Poznámky

The `My.Forms` object provides an instance of each form in the current project. The name of the property is the same as the name of the form that the property accesses.

You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification. Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance. For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.

The `My.Forms` object exposes only the forms associated with the current project. It does not provide access to forms declared in referenced DLLs. To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.

You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.

The object and its properties are available only for Windows applications.

## <a name="properties"></a>Vlastnosti

Each property of the `My.Forms` object provides access to an instance of a form in the current project. The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.

> [!NOTE]
> If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*. For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.

The `My.Forms` object provides access to the instance of the application's main form that was created on startup. For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it. Subsequent attempts to access that property return that instance of the form.

You can dispose of a form by assigning `Nothing` to the property for that form. The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value. If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.

You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator. You can use those operators to check if the value of the property is `Nothing`.

> [!NOTE]
> Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison. However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance. However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.

## <a name="example"></a>Příklad

This example changes the title of the default `SidebarMenu` form.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

For this example to work, your project must have a form named `SidebarMenu`.

This code will work only in a Windows Application project.

## <a name="requirements"></a>Požadavky

### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu

|Project type|K dispozici|
|---|---|
|Windows Application|**Yes**|
|Knihovna tříd|Ne|
|Konzolová aplikace|Ne|
|Windows Control Library|Ne|
|Web Control Library|Ne|
|Služba systému Windows|Ne|
|Web Site|Ne|

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objekty](../../../visual-basic/language-reference/objects/index.md)
- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Přístup k formulářům aplikace](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
