---
order: 0
title:
  zh-CN: 基本评论
  en-US: Basic comment
---

## zh-CN

一个基本的评论作者，头像，时间和行动。

## en-US

A basic comment with author, avatar, time and actions.

````jsx
import { Comment, Icon, Tooltip, Avatar } from 'antd';
import moment from 'moment';

class App extends React.Component {
  state = {
    likes: 0,
    dislikes: 0,
    action: null,
  }

  like = () => {
    this.setState({
      likes: 1,
      dislikes: 0,
      action: 'liked',
    });
  }

  dislike = () => {
    this.setState({
      likes: 0,
      dislikes: 1,
      action: 'disliked',
    })
  }

  render() {
    const { likes, dislikes, action } = this.state;

    const actions = [
      <span>
        <Tooltip title="Like">
          <Icon
            type="like"
            theme={action === 'liked' ? 'twoTone' : 'filled'}
            onClick={this.like}
          />
        </Tooltip>
        <span style={{ paddingLeft: 8, cursor: 'auto' }}>
          {likes}
        </span>
      </span>,
      <span>
        <Tooltip title="Dislike">
          <Icon
            type="dislike"
            theme={action === 'disliked' ? 'twoTone' : 'filled'}
            onClick={this.dislike}
          />
        </Tooltip>
        <span style={{ paddingLeft: 8, cursor: 'auto' }}>
          {dislikes}
        </span>
      </span>,
      <span>Reply to</span>,
    ];

    return (
      <Comment
        author={<a>Han Solo</a>}
        avatar={
          <Avatar
            src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
            alt="Han Solo"
          />
        }
        time={moment().fromNow()}
        tooltipTime={moment().format('YYYY-MM-DD HH:mm:ss')}
        actions={actions}
      >
        <p>Sagittis id consectetur purus ut faucibus pulvinar elementum integer enim. Pellentesque massa placerat duis ultricies lacus sed turpis. Tempus urna et pharetra pharetra massa massa.</p>
      </Comment>
    );
  }
}

ReactDOM.render(<App />, mountNode);
````