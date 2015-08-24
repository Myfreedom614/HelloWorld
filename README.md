# HelloWorld
UWP HelloWorld App using C++
MSDN document: https://msdn.microsoft.com/en-us/library/windows/apps/dn996906.aspx

To make VisualState works, one thing we need to note is adding x:Name for your container and control:

MainPage.xaml:
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup>
                <VisualState x:Name="wideState">
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="641" />
                    </VisualState.StateTriggers>
                </VisualState>
                <VisualState x:Name="narrowState">
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="0" />
                    </VisualState.StateTriggers>
                    <VisualState.Setters>
                        <Setter Target="contentPanel.Margin" Value="20,30,0,0"/>
                        <Setter Target="inputPanel.Orientation" Value="Vertical"/>
                        <Setter Target="inputButton.Margin" Value="0,4,0,0"/>
                    </VisualState.Setters>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>
        <StackPanel x:Name="contentPanel" Margin="120,30,0,0">
            <TextBlock HorizontalAlignment="Left" Text="Hello World" FontSize="36"/>
            <TextBlock Text="What's your name?" Style="{StaticResource BaseTextBlockStyle}" FontSize="16"/>
            <StackPanel x:Name="inputPanel" Orientation="Horizontal" Margin="0,20,0,20">
                <TextBox x:Name="nameInput" Width="300" HorizontalAlignment="Left"/>
                <Button x:Name="inputButton" Content="Say &quot;Hello&quot;" Click="Button_Click"/>
            </StackPanel>
            <TextBlock Style="{ThemeResource BaseTextBlockStyle}" FontSize="16" x:Name="greetingOutput"/>
        </StackPanel>
    </Grid>
