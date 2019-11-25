---
title: Vytváření vlastních součástí naslouchajících protokolům
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353613"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Návod: Vytváření vlastních součástí naslouchajících protokolům (Visual Basic)

This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.

## <a name="getting-started"></a>Začínáme

Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.

#### <a name="to-create-the-listener"></a>To create the listener

- In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.

     The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods. The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.

    > [!NOTE]
    > The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.

To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.

The next procedure provides some simple steps for creating a strongly named log-listener assembly. For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>To strongly name the log-listener assembly

1. Have a project selected in **Solution Explorer**. On the **Project** menu, choose **Properties**.

2. Click the **Signing** tab.

3. Select the **Sign the assembly** box.

4. Select **\<New>** from the **Choose a strong name key file** drop-down list.

     The **Create Strong Name Key** dialog box opens.

5. Provide a name for the key file in the **Key file name** box.

6. Enter a password in the **Enter password** and **Confirm password** boxes.

7. Click **OK**.

8. Rebuild the application.

## <a name="adding-the-listener"></a>Adding the Listener

Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.

The format of a strongly named type is as follows.

\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>To determine the strong name of the listener

- The following code shows how to determine the strongly named type name for `SimpleListener`.

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     The strong name of the type depends on your project.

With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>To add the listener to My.Application.Log

1. Right-click on app.config in the **Solution Explorer** and choose **Open**.

     -nebo-

     If there is an app.config file:

    1. On the **Project** menu, choose **Add New Item**.

    2. From the **Add New Item** dialog box, choose **Application Configuration File**.

    3. Click **Add**.

2. Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section. The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.

3. Add this element to the `<listeners>` section:

    ```xml
    <add name="SimpleLog" />
    ```

4. Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.

5. Add this element to that `<sharedListeners>` section:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Change the value of `SimpleLogStrongName` to be the strong name of the listener.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
